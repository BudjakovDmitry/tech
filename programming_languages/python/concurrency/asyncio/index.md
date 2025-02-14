# Asyncio

asyncio is a library to write concurrent code using the `async/await` syntax.

## Hello world

```python
import asyncio

async def main():
    print("Hello...")
    await asyncio.sleep(1)
    print("...World!")

asyncio.run(main())
```

asyncio provides a set of high-level APIs to:

- [run Python coroutines](coroutines_and_tasks.md) concurrently and have full control
over their execution.
