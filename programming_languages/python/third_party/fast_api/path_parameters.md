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
