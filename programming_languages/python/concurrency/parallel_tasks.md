# Launching parallel tasks

The `concurrent.futures` module provides a high-level interface for asynchronous
executing callables.

The asynchronous execution can be performed with threads, using `ThreadPoolExecutor`, or
separate processes, using `ProcessPoolExecutor`. Both implement the same interface,
which is defined by the abstract `Executor` class.

Generally speaking the best practice for using threads is to use `ThreadPoolExecutor`
class from the `concurrent.futures` module, passing all required data in though the
`submit()` method.

## Executor objects

An abstract class that provides methods to execute calls asynchronously. It should not
be used directly, but through its concrete subclasses.

### submit

```python
submit(fn, /, *args, **kwargs)
```

Schedule the callable *fn*,, to be executed as `fn(*args, **kwargs)` and returns a
`Future` object representing the execution of the callable.

```python
from concurrent.futures import ThreadPoolExecutor

with ThreadPoolExecutor(max_workers=1) as executor:
    future = executor.submit(pow, 323, 1235)
    print(future.result())
```

### shutdown

```python
shutdown(wait=True, *, cancel_futures=False)
```

Signal the executor that it should free any resources that it is using when the
currently pending futures are done executing. Calls `Executor.submit()` and
`Executor.map()` made after shutdown will raise `RuntimeError`.

If *wait* is `True` then this method will not return until all the pending futures are
done executing and the resources associated with the executor have been freed. If *wait*
is `False` then this method will return immediately and the resources, associated with
the executor will be freed when all pending futures are done executing. Regardless of
the value of *wait*, the entire Python program will not exit until all pending futures
are done executing.

If *cancel_futures* is `True`, this method will cancel all pending futures that the
executor has not started running. Any futures that are completed or running won't be
cancelled, regardless of the value of *cancel_futures*.

If both *cancel_futures* and *wait* are `True`, all futures that the executor has
started running will be completed prior to this method returning. The remaining futures
are cancelled.

You can avoid having to call this method explicitly if you use the `with` statement,
which will shutdown the `Executor` (waiting as if `Executor.shutdown()` were called
with *wait* to set `True`).

## ThreadPoolExecutor

`ThreadPoolExecutor` is an `Executor` subclass that uses a pool of threads to execute
calls asynchronously.

## ProcessPoolExecutor

The `ProcessPoolExecutor` class is an `Executor` subclass that uses a pool of processes
to execute calls asynchronously.
