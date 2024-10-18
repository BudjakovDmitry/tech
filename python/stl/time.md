# time

## time.sleep(secs)

Suspend execution of the calling thread for the given number of seconds. The argument
may be a floating-point number to indicate a more precise sleep time.

The suspension time may be longer than requested by an arbitrary amount because of the
scheduling of other activity in the system.

If the sleep is interrupted be a signal and no exception is raised by the signal
handler, the sleep is restarted with a recomputed timeout.

```python
import time

time.sleep(5)
```