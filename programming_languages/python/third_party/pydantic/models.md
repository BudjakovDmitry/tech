# Models

One of the primary ways of defining schema in Pydantic is via models. Models are simply
classes which inherit from `BaseModel` and define fields as annotated attributes.

Untrusted data can be passed to a model and, after parsing and validation, Pydantic
guarantees that the fields of the resultant model instance will conform to the field
types defined on the model.

```python
from pydantic import BaseModel, ConfigDict


class User(BaseModel):
    id: int
    name: str = 'Jane Doe'

    model_config = ConfigDict(str_max_length=10)

    
# The model can then be instantiated
user = User(id='123')


assert user.name == 'Jane Doe'  
assert user.id == 123  
assert isinstance(user.id, int)

# By default, models are mutable and field values can be changed
# through attribute assignment:
user.id = 321
assert user.id == 321
```

In this example, `User` is a model with two fields:

* `id`, which is an integer and is required
* `name`, which is a string and is not required (it has a default value).

`user` is an instance of `User`. Initialization of the object will perform all parsing
and validation. If no `ValidationError` exception is raised, you know the resulting
model instance is valid.

The model instance can be serialized using the `model_dump()` method:

```python
assert user.model_dump() == {'id': 123, 'name': 'Jane Doe'}
```

Calling `dict` on the instance will also provide a dictionary, but nested fields will
not be recursively converted into dictionaries. `model_dump()` also provides numerous
arguments to customize the serialization result.

> When defining your models, watch out for naming collisions between your field name and
> its type annotation.
> 
> For example, the following will not behave as expected and would yield a validation
> error:
> 
> ```python
> from typing import Optional
>
> from pydantic import BaseModel
>
>
> class Boo(BaseModel):
>     int: Optional[int] = None
>
>
> m = Boo(int=123)  # Will fail to validate.
> ```
