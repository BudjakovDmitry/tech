# Request body

To declare a request body, you use Pydantic models.

> To send data, you should use one of: `POST` (the more common), `PUT`, `DELETE` or
> `PATCH`.
> 
> Sending a body with a `GET` request has an undefined behavior in the specifications,
> nevertheless, it is supported by FastAPI, only for very complex/extreme use cases.
> 
> The interactive docs with Swagger UI won't show the documentation for the body when
> using `GET`, and proxies in the middle might not support it.


```python
from fastapi import FastAPI
from pydantic import BaseModel


class Item(BaseModel):
    name: str
    description: str | None = None
    price: float
    tax: float | None = None


app = FastAPI()


@app.post("/items/")
async def create_item(item: Item):
    item_dict = item.dict()
    if item.tax is not None:
        price_with_tax = item.price + item.tax
        item_dict.update({"price_with_tax": price_with_tax})
    return item
```

1. Declare your data model as a class that inherits from `BaseModel`.

When a model attribute has a default value, it is not required. Otherwise, it is
required. Use `None` to make it just optional.

You can declare path parameters and request body at the same time. FastAPI will
recognize that the function parameters that match path parameters should be taken from
the path, and that function parameters that are declared to be Pydantic models should be
taken from the request body.

```python
from fastapi import FastAPI
from pydantic import BaseModel


class Item(BaseModel):
    name: str
    description: str | None = None
    price: float
    tax: float | None = None


app = FastAPI()


@app.put("/items/{item_id}")
async def update_item(item_id: int, item: Item):
    return {"item_id": item_id, **item.dict()}
```

You can also declare body, path and query parameters, all at the same time. FastAPI will
recognize each of them and take the data from the correct place.

```python
from fastapi import FastAPI
from pydantic import BaseModel


class Item(BaseModel):
    name: str
    description: str | None = None
    price: float
    tax: float | None = None


app = FastAPI()


@app.put("/items/{item_id}")
async def update_item(item_id: int, item: Item, q: str | None = None):
    result = {"item_id": item_id, **item.dict()}
    if q:
        result.update({"q": q})
    return result
```

The function parameters will be recognized as follows:

* If the parameter is also declared in the path, it will be used as a path parameter.
* If the parameter is of a singular type (like `int`, `float`, `str`, `bool`, etc.) it
will be interpreted as a query parameter.
* If the parameter is declared to be of the type of Pydantic model, it will be
interpreted as a request body.
