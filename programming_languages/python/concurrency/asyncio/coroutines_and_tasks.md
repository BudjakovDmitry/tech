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

### asyncio.run()

The `asyncio.run()` function to run the top-level entry point "main()" function
(example above).

### Awaiting on a coroutine

The following snippet of code will print "hello" after waiting for 1 second, and then
print "world" after waiting for another 2 seconds.

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

### asyncio.create_task()

The `asyncio.create_task()` function to run coroutines concurrently as asyncio `Tasks`.

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

### asyncio.TaskGroup

Added in version 3.11

The `asyncio.TaskGroup` class provides a more modern alternative to `create_task()`.

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
