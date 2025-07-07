# Loguru - Introduction to Logging in Python

## Why Not Just Use `print()`?

If you're debugging or monitoring a Python script, you might be tempted to use `print()` to track what’s happening. While `print()` is quick and simple, it's not scalable or flexible for real-world development.

Here’s why `print()` falls short:
- It doesn’t show **timestamps** or **log levels** (e.g., info, warning, error).
- It’s difficult to turn off in production.
- You can’t easily log to **files**, **remote systems**, or **filter logs**.
- It lacks **structured formatting** and **exception handling**.

That’s where **[Loguru](https://github.com/Delgan/loguru)** comes in—a modern, user-friendly logging library that solves these problems with minimal setup.

## Basic Usage
Loguru replaces traditional logging with a simple, intuitive interface.
If you had a python script called `app.py` which looked like this:

```python
from loguru import logger

logger.debug("This is a debug message")
```

Executing `app.py` would give this output
```
2025-05-23 14:16:33.051 | DEBUG    | __main__:<module>:3 - This is a debug message
```

With the default format, the output contains the following details:
- Timestamp: `2025-07-07 10:00:00.123`
- Log level: `DEBUG`. This descriubes the severity level of the log message
- Source (the file location, scope, and line number): `__main__:<module>:3`. In this example, the file location is __main__ because you executed the app.py file directly. The scope is <module> because the logger is not located inside a class or a function.
- Message: `This is a debug message`

## Logging Levels

In the example above we used `logger.debug` which logged a message at the `DEBUG` level. Loguru offers 7 unique log levels.
They specify the severity of a log record so that messages can be filtered or prioritized based on how urgent they are. Each level is associated with an integer value as shown in the table below:

| Level      | Value | Used to record...                                                                                                  |
| ---------- | ------|------------------------------------------------------------------------------------------------------------------- |
| `TRACE`    | 5     | Fine-grained information about the program's execution path for diagnostic purposes.                               |
| `DEBUG`    | 10    | Messages for debugging purposes                                                                                    |
| `INFO`     | 20    | Informational messages that describe the normal operation of the program. (e.g., starting run, finished execution) |
| `SUCCESS`  | 25    | The success of an operation. Similar to `INFO`                                                                     |
| `WARNING`  | 30    | Unexpected events that aren’t errors yet and may require further investigation                                     |
| `ERROR`    | 40    | An error that affects a specific operation                                                                         |
| `CRITICAL` | 50    | Record error conditions that prevent a core function from working.                                                 |

Each log level listed above has a corresponding method of the same name, which enables you to send log records with that log level:

```python
from loguru import logger

logger.trace("A trace message.")
logger.debug("A debug message.")
logger.info("An info message.")
logger.success("A success message.")
logger.warning("A warning message.")
logger.error("An error message.")
logger.critical("A critical message.")
```

Output:
```
2025-05-23 14:18:03.342 | DEBUG    | __main__:<module>:4 - A debug message.
2025-05-23 14:18:03.342 | INFO     | __main__:<module>:5 - An info message.
2025-05-23 14:18:03.342 | SUCCESS  | __main__:<module>:6 - A success message.
2025-05-23 14:18:03.342 | WARNING  | __main__:<module>:7 - A warning message.
2025-05-23 14:18:03.342 | ERROR    | __main__:<module>:8 - An error message.
2025-05-23 14:18:03.342 | CRITICAL | __main__:<module>:9 - A critical message.
```

Notice that the `TRACE` level message is not included in the output above. This is because Loguru defaults to using `DEBUG` as its minimum level, which causes any logs with a severity lower than `DEBUG` to be ignored.

## Changing the default log level

If you want to change the default level, you have to overwrite the default handler:

```python
from loguru import logger
import sys

logger.remove(0)
logger.add(sys.stderr, level="INFO")
```

The `remove()` method is called first to remove the configuration for the default handler (whose ID is 0). To remove all existing handlers, call the remove function with no arguments:

```python
logger.remove()
```

Subsequently, the `add()` method adds a new handler to the logger. This handler logs to the standard error and only records logs with `INFO` severity or greater.

> NOTE: Here, `sys.stderr` is the argument to the `sink` parameter which determines where the logs go.

## Logging Exceptions

Loguru makes exception logging a breeze:

```python
try:
    1 / 0
except ZeroDivisionError:
    logger.exception("Oops! Something went wrong.")
```

This logs the full traceback automatically with no manual formatting needed.

## Logging to a File

You can save logs to an output file using the `sink` parameter in `logger.add()`:

```python
logger.add("app.log", level="INFO")
```
> NOTE: The line above can be written explicitly as `logger.add(sink="app.log", level="INFO")`

When `sink` points to a file, the `add()` method provides a few more options for customizing how the log file should be handled.
Here are the ones I think are most useful:

* **delay**: if set to `True`, the creation of a new log file will be delayed until the first log message is pushed.
* **level**: Only log messages at this level or higher.


## References/Resources
- [Better Stack](https://betterstack.com/community/guides/logging/loguru/)
- [Loguru Docs](https://loguru.readthedocs.io/en/stable/overview.html)
- [Real Python](https://realpython.com/python-loguru/)