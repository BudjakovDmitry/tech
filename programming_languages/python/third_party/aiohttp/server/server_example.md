# Server Example

```python
from aiohttp import web


async def handle(request: web.Request) -> web.Response:
    name = request.match_info.get('name', 'Anonymous')
    text = f'Hello, {name}'
    return web.Response(text=text)

app = web.Application()
app.add_routes([
    web.get('/', handle),
    web.get('/{name}, handle')
])
```

