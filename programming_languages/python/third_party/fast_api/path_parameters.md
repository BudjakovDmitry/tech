# Path parameters

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/{item_id}")
async def read_item(item_id):
    return {"item_id": item_id}
```

The value of the path parameter `item_id` will be passed to your function as the
argument `item_id`.

## Data validation and data conversion

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

## Order matters

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

## Predefined values

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

## Path parameters containing paths

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
