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

### Futures

A `Future` is a special __low-level__ awaitable object that represents an __eventual
result__ of an asynchronous operation.

When a `Future` object is awaited it means that the coroutine will wait until the
`Future` is resolved in some other place.

Future objects in asyncio are needed to allow callback-based code to be used with
async/await.

Normally __there is no need__ to create Future objects at the application level code.

Future objects, sometimes exposed by libraries and some asyncio APIs, can be awaited:

```python
async def main():
    await function_that_returns_a_future_object()

    # this is also walid
    await asyncio.gather(
        function_that_returns_a_future_object(),
        some_python_coroutine(),
    )
```

## Creating tasks

### asyncio.create_task()

```python
asyncio.create_task(coro, *, name=None, context=None)
```

Wrap the _coro_ coroutine into a `Task` and schedule its execution. Return the `Task`
object.

If _name_ is not None, it is set as the name of the task using `Task.set_name()`.

An optional keyword-only _context_ argument allows specifying a custom
`contextvars.Context` for the _coro_ to run in. The current context copy is created when
no _context_ is provided.

The task is executed in the loop returned by `get_running_loop()`, `RuntimeError` is
raised if there is no running loop in current thread.

> __Important__: Save a reference to the result of this function, to avoid a task
> disappearing mid-execution. The event loop only keeps weak references to tasks. A task
> that isn’t referenced elsewhere may get garbage collected at any time, even before
> it’s done. For reliable “fire-and-forget” background tasks, gather them in a
> collection:

```python
background_tasks = set()

for i in range(10):
    task = asyncio.create_task(some_coro(param=i))

    # Add task to the set. This creates a strong reference
    background_tasks.add(task)

    # To prevent keeping references to finished tasks forever,
    # make each task remove its own reference from the set after completion:
    task.add_done_callback(background_tasks.discard)
```
