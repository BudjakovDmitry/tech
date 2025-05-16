# APIRouter

Let's say we have a complex application with many entities.

We want to have the path operations related to different entities separated from each
other, to keep code organized. For example:

* `/app/routers/users.py` - module that handle users routes
* `/app/routers/items.py` - module that handle items routes

We can create the path operations for each module using `APIRouter`.

```python
from fastapi import APIRouter

router = APIRouter()


@router.get("/users/", tags=["users"])
async def read_users():
    return [{"username": "Rick"}, {"username": "Morty"}]


@router.get("/users/me", tags=["users"])
async def read_user_me():
    return {"username": "fakecurrentuser"}


@router.get("/users/{username}", tags=["users"])
async def read_user(username: str):
    return {"username": username}
```

You can think of `APIRouter` as a "mini `FastAPI`" class. All the same options are
supported. All the same `parameters`, `responses`, `dependencies`, `tags`, etc.

The code above can be smaller and simplify a bit:

```python
from fastapi import APIRouter

router = APIRouter(
    prefix="/users",  # all endpoints of this router have the same prefix
    tags=["users"],
)


@router.get("/")
async def read_users():
    return [{"username": "Rick"}, {"username": "Morty"}]


@router.get("/me")
async def read_user_me():
    return {"username": "fakecurrentuser"}


@router.get("/{username}")
async def read_user(username: str):
    return {"username": username}
```
