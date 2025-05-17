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
- [Path and query parameters](parameters.md)
- [Request body](request_body.md)
- [Response model - return type](response.md)
- [Path operation configuration](path_operation_configuration.md)
- [Metadata and Docs URLs](api_metadata.md)
- [APIRouter](apirouter.md)
