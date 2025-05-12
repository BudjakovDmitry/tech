# FastAPI

```python
from fastapi import FastAPI


app = FastAPI()


@app.get("/")
async def root():
    return {"message": "Hello World"}
```

## Content

- [Installation](installation.md)
- [Run server](run_server.md)
- [Interactive API docs](api_docs.md)
- [Methods](methods.md)
- [Path parameters](path_parameters.md)
