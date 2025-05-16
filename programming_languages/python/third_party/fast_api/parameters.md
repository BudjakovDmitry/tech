# Parameters

## Path parameters

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/{item_id}")
async def read_item(item_id):
    return {"item_id": item_id}
```

The value of the path parameter `item_id` will be passed to your function as the
argument `item_id`.

### Data validation and data conversion

You can declare the type of path parameter in the function:

```python
@app.get("/items/{item_id}")
async def read_item(item_id: int):
    return {"item_id": item_id}
```

With this type decoration, FastAPI gives you automatic request "parsing" and data
validation. `item_id` (received and returned) has type `int`. If you try `/items/foo` or
`/items/4.2` you will see an HTTP error:

```
{
  "detail": [
    {
      "type": "int_parsing",
      "loc": [
        "path",
        "item_id"
      ],
      "msg": "Input should be a valid integer, unable to parse string as an integer",
      "input": "foo"
    }
  ]
}
```

because the path parameter `item_id` had a value which is not an `int`.

All the data validation is performed under the good by Pydantic.

### Order matters

When creating path operations, you can find situations where you have a fixed path. Like
`/users/me`. And then you can also have a path `/users/{user_id}` to get data about a
specific user by some user ID.

Because path operations are evaluated in order, you need to make sure that the path for
`/users/me` is declared before the one for `/users/{user_id}`:

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/users/me")
async def read_user_me():
    return {"user_id": "the current user"}


@app.get("/users/{user_id}")
async def read_user(user_id: str):
    return {"user_id": user_id}
```

Otherwise, the path for `/users/{user_id}` would match also for `/users/me`, "thinking"
that it's receiving a parameter `user_id` with a value of `"me"`.

### Predefined values

If you have a path operation that receives a path parameter, but you want the possible
valid path parameter values to be predefined, you can use a standard Python `Enum`.

Create a subclass that inherits from str and from `StrEnum`. Then create class
attributes with fixed values, which will be the available valid values:

```python
from enum import StrEnum

from fastapi import FastAPI


class ModelName(StrEnum):
    alexnet = "alexnet"
    resnet = "resnet"
    lenet = "lenet"


app = FastAPI()


@app.get("/models/{model_name}")
async def get_model(model_name: ModelName):
    # The value of the path parameter will be an enumeration member.
    if model_name is ModelName.alexnet:
        return {"model_name": model_name, "message": "Deep Learning FTW!"}

    if model_name.value == "lenet":
        return {"model_name": model_name, "message": "LeCNN all the images"}

    return {"model_name": model_name, "message": "Have some residuals"}
```

You can return enum members from your path operation, even nested in a JSON body (e.g. a
dict). They will be converted to their corresponding values (strings in this case)
before returning them to the client:

```python
return {"model_name": model_name, "message": "Deep Learning FTW!"}
```

In your client you will get a JSON response like:

```json
{
  "model_name": "alexnet",
  "message": "Deep Learning FTW!"
}
```

> You could also use `Enums` the same way with query parameters 

### Path parameters containing paths

Let's say you have a path operation with a path `/files/{file_path}`. But you need
`file_path` itself to contain a path, like `home/johndoe/myfile.txt`. So, the URL for
that file would be something like: `/files/home/johndoe/myfile.txt`.

OpenAPI doesn't support a way to declare a path parameter to contain a path inside.
Nevertheless, you can still do it in FastAPI, using one of the internal tools from
Starlette. And the docs would still work, although not adding any documentation telling
that the parameter should contain a path.

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/files/{file_path:path}")
async def read_file(file_path: str):
    return {"file_path": file_path}
```

> You could need the parameter to contain `/home/johndoe/myfile.txt`, with a leading
> slash (`/`). In that case, the URL would be: `/files//home/johndoe/myfile.txt`, with a
> double slash (`//`) between files and home.

---

## Query parameters

When you declare other function parameters that are not part of the path parameters,
they are automatically interpreted as "query" parameters.

```python
from fastapi import FastAPI

app = FastAPI()

fake_items_db = [{"item_name": "Foo"}, {"item_name": "Bar"}, {"item_name": "Baz"}]


@app.get("/items/")
async def read_item(skip: int = 0, limit: int = 10):
    return fake_items_db[skip : skip + limit]
```

How query parameters look like: `http://127.0.0.1:8000/names/?skip=0&limit=10`

### Defaults

As query parameters are not a fixed part of a path, they can be optional and can have
default values.

In the example above they have default values of `skip=0` and `limit=10`.

So, going to the URL: `http://127.0.0.1:8000/items/` would be the same as going to:
`http://127.0.0.1:8000/items/?skip=0&limit=10`

### Optional parameters

The same way, you can declare optional query parameters, by setting their default to
`None`:

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/items/{item_id}")
async def read_item(item_id: str, q: str | None = None):
    if q:
        return {"item_id": item_id, "q": q}
    return {"item_id": item_id}
```

In this case, the function parameter q will be optional, and will be `None` by default.

> Also notice that FastAPI is smart enough to notice that the path parameter `item_id`
> is a path parameter and `q` is not, so, it's a query parameter.

### Query parameter type conversion

You can also declare `bool` types, and they will be converted:

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/items/{item_id}")
async def read_item(item_id: str, q: str | None = None, short: bool = False):
    item = {"item_id": item_id}
    if q:
        item.update({"q": q})
    if not short:
        item.update(
            {"description": "This is an amazing item that has a long description"}
        )
    return item
```

In this case

* `http://127.0.0.1:8000/items/foo?short=1` or
* `http://127.0.0.1:8000/items/foo?short=True` or
* `http://127.0.0.1:8000/items/foo?short=true` or
* `http://127.0.0.1:8000/items/foo?short=on` or
* `http://127.0.0.1:8000/items/foo?short=yes`

or any other case variation (uppercase, first letter in uppercase, etc.), your function
will see the parameter `short` with a `bool` value of `True`. Otherwise, as `False`.

### Required query parameters

When you declare a default value for non-path parameters, then it is not required. If
you don't want to add a specific value but just make it optional, set the default as
`None`. But when you want to make a query parameter required, you can just not declare
any default value:

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/items/{item_id}")
async def read_user_item(item_id: str, needy: str):
    item = {"item_id": item_id, "needy": needy}
    return item
```

Here the query parameter `needy` is a required query parameter of type `str`.

As `needy` is a required parameter, you would need to set it in the URL:
`http://127.0.0.1:8000/items/foo-item?needy=sooooneedy`

> You could also use `Enums` the same way as with path parameters.

You can declare that a parameter can accept `None`, but that it's still required. This
would force clients to send a value, even if the value is `None`.

```python
@app.get("/items/")
async def read_items(q: str | None):
    ...
```

## Multiple path and query parameters

You can declare multiple path parameters and query parameters at the same time, FastAPI
knows which is which. And you don't have to declare them in any specific order. They
will be detected by name:

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/users/{user_id}/items/{item_id}")
async def read_user_item(
    user_id: int, item_id: str, q: str | None = None, short: bool = False
):
    item = {"item_id": item_id, "owner_id": user_id}
    if q:
        item.update({"q": q})
    if not short:
        item.update(
            {"description": "This is an amazing item that has a long description"}
        )
    return item
```

## Additional validation

FastAPI allows you to declare additional information and validation for your parameters.
Let's take this application as example:

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/items/")
async def read_items(q: str | None = None):
    results = {"items": [{"item_id": "Foo"}, {"item_id": "Bar"}]}
    if q:
        results.update({"q": q})
    return results
```

We are going to enforce that even though `q` is optional, whenever it is provided, its
__length doesn't exceed 50 characters__.

To achieve that we need `fastapi.Query` and `typing.Annotated`.

```python
from typing import Annotated

from fastapi import FastAPI, Query

app = FastAPI()


@app.get("/items/")
async def read_items(
        q: Annotated[str | None, Query(min_length=3, max_length=50)] = None
):
    results = {"items": [{"item_id": "Foo"}, {"item_id": "Bar"}]}
    if q:
        results.update({"q": q})
    return results
```

FastAPI will now:

* Validate the data making sure that the max length is 50 characters and min length is 3
characters
* Show a clear error for the client when the data is not valid
* Document the parameter in the OpenAPI schema path operation (so it will show up in the
automatic docs UI)

> Keep in mind that when using `Query` inside of `Annotated` you cannot use the
> `default` parameter for `Query`. Instead, use the actual default value of the function
> parameter. Otherwise, it would be inconsistent.

```python
# this is not allowed because it's not clear
# if the default value should be "rick" or "morty".
q: Annotated[str, Query(default="rick")] = "morty"
```

Other validations:

* `Query(pattern="^fixedquery$")` define a regular expressions pattern that the
parameter should match;

When you need to declare a value as required while using `Query`, you can simply not
declare a default value:

```python
from fastapi import FastAPI, Query
from typing import Annotated

app = FastAPI()


@app.get("/items/")
async def read_items(q: Annotated[str, Query(min_length=3)]):
    results = {"items": [{"item_id": "Foo"}, {"item_id": "Bar"}]}
    if q:
        results.update({"q": q})
    return results
```

## Metadata about the parameter

### Title and description

```python
from typing import Annotated

from fastapi import FastAPI, Query

app = FastAPI()


@app.get("/items/")
async def read_items(
    q: Annotated[
        str | None,
        Query(
            title="Query string",
            description="Query string for the items to search in the database that have a good match",
            min_length=3,
        ),
    ] = None,
):
    results = {"items": [{"item_id": "Foo"}, {"item_id": "Bar"}]}
    if q:
        results.update({"q": q})
    return results
```

### alias

Imagine that you want the parameter to be `item-query`. Like in:
`http://127.0.0.1:8000/items/?item-query=foobaritems`. But `item-query` is not a valid
Python variable name.

Then you can declare an `alias`, and that alias is what will be used to find the
parameter value:

```python
from typing import Annotated

from fastapi import FastAPI, Query

app = FastAPI()


@app.get("/items/")
async def read_items(q: Annotated[str | None, Query(alias="item-query")] = None):
    results = {"items": [{"item_id": "Foo"}, {"item_id": "Bar"}]}
    if q:
        results.update({"q": q})
    return results
```

### Deprecating parameters

```python
from typing import Annotated

from fastapi import FastAPI, Query

app = FastAPI()


@app.get("/items/")
async def read_items(
    q: Annotated[
        str | None,
        Query(
            alias="item-query",
            title="Query string",
            description="Query string for the items to search in the database that have a good match",
            min_length=3,
            max_length=50,
            pattern="^fixedquery$",
            deprecated=True,
        ),
    ] = None,
):
    results = {"items": [{"item_id": "Foo"}, {"item_id": "Bar"}]}
    if q:
        results.update({"q": q})
    return results
```

### Exclude parameter from OpenAPI

Exclude a query parameter from the generated OpenAPI schema (and thus, from the
automatic documentation systems):

```python
from typing import Annotated

from fastapi import FastAPI, Query

app = FastAPI()


@app.get("/items/")
async def read_items(
    hidden_query: Annotated[str | None, Query(include_in_schema=False)] = None,
):
    if hidden_query:
        return {"hidden_query": hidden_query}
    else:
        return {"hidden_query": "Not found"}
```

## Query parameter list / multiple values

When you define a query parameter explicitly with `Query` you can also declare it to
receive a list of values, or said in another way, to receive multiple values.

For example, to declare a query parameter `q` that can appear multiple times in the URL,
you can write:

```python
from typing import Annotated

from fastapi import FastAPI, Query

app = FastAPI()


@app.get("/items/")
async def read_items(q: Annotated[list[str] | None, Query()] = None):
    query_items = {"q": q}
    return query_items
```

Then, with a URL like: `http://localhost:8000/items/?q=foo&q=bar` you would receive the
multiple `q` query parameters' values (`foo` and `bar`) in a Python list inside your
path operation function, in the function parameter `q`.

> To declare a query parameter with a type of list, like in the example above, you need
> to explicitly use `Query`, otherwise it would be interpreted as a request body.

You can also define a default list of values if none are provided:

```python
from typing import Annotated

from fastapi import FastAPI, Query

app = FastAPI()


@app.get("/items/")
async def read_items(q: Annotated[list[str], Query()] = ["foo", "bar"]):
    query_items = {"q": q}
    return query_items
```

If you go to: `http://localhost:8000/items/` the default of `q` will be:
`["foo", "bar"]`.

You can also use `list` directly instead of `list[str]`:

```python
from typing import Annotated

from fastapi import FastAPI, Query

app = FastAPI()


@app.get("/items/")
async def read_items(q: Annotated[list, Query()]):
    query_items = {"q": q}
    return query_items
```

> Keep in mind that in this case, FastAPI won't check the contents of the list. For
> example, `list[int]` would check (and document) that the contents of the list are
> integers. But `list` alone wouldn't.
