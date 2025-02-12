# Handler

A request handler must be a coroutine that accept a *Request* instance as its only
parameter and return a *Response* instance.

```python
from aiohttp import web

async def hello(request):
    return web.Response(text="Hello, world")
```
