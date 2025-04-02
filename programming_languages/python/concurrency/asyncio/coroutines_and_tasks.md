# Coroutines and tasks

## Coroutines

Coroutines declared with the `async/await` syntax is the preferred way of writing
asyncio applications.

```python
import asyncio

async def main():
    print('hello')
    await asyncio.sleep(1)
    print('world')

asyncio.run(main())
# prints "hello", waits 1 second and prints "world"
```

Note that simply calling a coroutine will not schedule it to be executed.

```python
>>> main()
<coroutine object main ...>
```

To run a coroutine asyncio provides a following mechanism:

* The `asyncio.run()` function to run the top-level entry point "main()" function
(example above).

* Awaiting on a coroutine. The following snippet of code will print "hello" after
waiting for 1 second, and then print "world" after waiting for another 2 seconds.

```python
import asyncio
import time

async def say_after(delay, what):
    await asyncio.sleep(delay)
    print(what)

async def main():
    print(f"started at {time.strftime('%X')}")
    
    await say_after(1, 'hello')
    await say_after(2, 'world')
    
    print(f"finished at {time.strftime('%X')}")

asyncio.run(main())
```

* The `asyncio.create_task()` function to run coroutines concurrently as asyncio
`Tasks`.

Let's modify the above example and run two `say_after` coroutines _concurrently_.

```python
import asyncio


async def main():
    task1 = asyncio.create_task(say_after(1, 'hello'))
    task2 = asyncio.create_task(say_after(2, 'world'))

    print(f"started at {time.strftime('%X')}")
    
    # wait until both tasks are completed
    # (should take around 2 seconds)
    await task1
    await task2
    
    print(f"finished at {time.strftime('%X')}")
```

* The `asyncio.TaskGroup` class provides a more modern alternative to `create_task()`.

Added in version 3.11

```python
import asyncio

async def main():
    async with asyncio.TaskGroup() as tg:
        task1 = tg.create_task(say_after(1, 'hello'))
        task2 = tg.create_task(say_after(2, 'world'))

        print(f"started at {time.strftime('%X')}")
        
   # The await is implicit when the context manager exits.

   print(f"finished at {time.strftime('%X')}")
```

## Awaitables

We say that an object is an awaitable object if it can be used in an `await` expression.
Many asyncio APIs are designed to accept awaitables.

There are three main types of _awaitable_ objects:

- coroutines;
- Tasks;
- Futures.

### Coroutines

Python coroutines are awaitables and therefore can be awaited from other coroutines:

```python
import asyncio

async def nested():
    return 42

async def main():
    nested()  # will raise a "RuntimeWarning": cocoutine 'nested' was never awaited
    # Nothing happens if we just call "nested()"
    # A coroutine object is created but not awaited,
    # so it *won't run at all*

    # Let's do it differently now and await it.
    print(await nested())  # will print 42

asyncio.run(main())
```

> __Important__: the term "coroutine" can be used for two closely related concepts:
> * a _coroutine function_: an `async def` function;
> * a _coroutine object_: an object returned by calling a _coroutine function_.

### Tasks

Tasks are used to schedule coroutiles _concurrently_.

When a coroutine is wrapped into a _Task_ with functions like `asyncio.create_task()`
the coroutine is automatically scheduled to run soon.

```python
import asyncio

async def nested():
    return 42

async def main():
    task = asyncio.create_task(nested())
    await task


asyncio.run(main())
```
