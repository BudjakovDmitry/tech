# Response model - return type

You can declare the type used for the response by annotating the _path operation
function_ return type. You can use type annotations the same way you would for input
data in function parameters, you can use Pydantic models, lists, dictionaries, scalar
values like integers, booleans, etc.

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()


class Item(BaseModel):
    name: str
    description: str | None = None
    price: float
    tax: float | None = None
    tags: list[str] = []


@app.post("/items/")
async def create_item(item: Item) -> Item:
    return item


@app.get("/items/")
async def read_items() -> list[Item]:
    return [
        Item(name="Portal Gun", price=42.0),
        Item(name="Plumbus", price=32.0),
    ]
```

FastAPI will use this return type to:

* __Validate__ the returned data.
  * If the data is invalid (e.g. you are missing a field), it means that your app code
  is broken, not returning what it should, and it will return a server error instead of
  returning incorrect data. This way you and your clients can be certain that they will
  receive the data and the data shape expected.
* It will __limit and filter__ the output data to what is defined in the return type.
* Add a JSON Schema for the response, in the OpenAPI path operation.
  * This will be used by the automatic docs.
  * It will also be used by automatic client code generation tools.

# `response_model` parameter

There are some cases where you need or want to return some data that is not exactly what
the type declares. For example, you could want to return a dictionary or a database
object, but declare it as a Pydantic model. This way the Pydantic model would do all the
data documentation, validation, etc. for the object that you returned (e.g. a dictionary
or database object). If you added the return type annotation, tools and editors would
complain with a (correct) error telling you that your function is returning a type (e.g.
a `dict`) that is different from what you declared (e.g. a Pydantic model). In those
cases, you can use the _path operation decorator_ parameter `response_model` instead of
the return type.

You can use the `response_model` parameter in any of the path operations:

* `@app.get()`
* `@app.post()`
* `@app.put()`
* `@app.delete()`
* etc

```python
from typing import Any

from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()


class Item(BaseModel):
    name: str
    description: str | None = None
    price: float
    tax: float | None = None
    tags: list[str] = []


@app.post("/items/", response_model=Item)
async def create_item(item: Item) -> Any:
    return item


@app.get("/items/", response_model=list[Item])
async def read_items() -> Any:
    return [
        {"name": "Portal Gun", "price": 42.0},
        {"name": "Plumbus", "price": 32.0},
    ]
```
