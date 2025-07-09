# Introduction to Testing

Testing is the process of checking that your code behaves as expected. It helps ensure that your software is correct, reliable, and maintainable—especially as it grows or changes over time.

In its simplest form, testing answers the question:

> "Does this piece of code do what it's supposed to do?"

#### Why Testing Is Important
* **Catch bugs early**: Tests can alert you to issues before they make it to production.
* **Prevent regressions**: If something breaks due to a new change, tests help you catch it quickly.
* **Make refactoring safer**: Want to clean up messy code? With tests in place, you can refactor with confidence.
* **Document behavior**: Well-written tests serve as living documentation that shows how your code is intended to work.
* **Support collaboration**: In team environments, tests help ensure that one developer's changes don't accidentally break someone else’s work.

#### Types of Tests
There are several types of tests in software development:

* **Unit tests**: Test individual functions or methods in isolation.
* **Integration tests**: Test how different parts of the system work together.
* **End-to-end (E2E) tests**: Simulate real user interactions with the full system.

This guide focuses on **unit testing**, the foundation of a reliable testing strategy.


## Unit Testing in Python with `pytest`
`pytest` is a powerful, easy-to-use testing framework for Python that makes it simple to:

- Write clear and concise test cases
- Automatically discover and run tests
- Use advanced features like fixtures, parameterization, and test categorization
- Generate coverage reports

It's more readable and feature-rich than Python’s built-in `unittest` module, and it's widely used in modern Python projects.

### Installation

```bash
uv pip install pytest pytest-cov
```

### Getting Started

> **A test is just a function named with the prefix `test_` which has an assertion.**

To create a basic test, create a file within the `tests` directory in the root of your repository.
Here's an example:

```python
# test_math.py
def add(a, b):
    return a + b

def test_add():
    assert add(2, 3) == 5
```

**A test is all about checking outputs against expectations**. This is why a test is simply an **assertion** that an output matches an expectation.

To run this test, simply execute the pytest command:

```bash
pytest
```

By default, pytest will look for files that start with `test_` or end in `_test.py` and execute all functions that start with `test_`.

Here are some other examples of tests:

```python
def test_uppercase():
    assert "loud noises".upper() == "LOUD NOISES"

def test_reversed():
    assert list(reversed([1, 2, 3, 4])) == [4, 3, 2, 1]

def test_some_primes():
    assert 37 in {
        num
        for num in range(2, 50)
        if not any(num % div == 0 for div in range(2, num))
    }
```

> TIP: **It's good practice to keep your tests concise by having one assertion per test.**

### Using Fixtures

Fixtures let you create reusable setup/teardown logic for tests (like database connections, mock data, or temp files).

```python
import pytest

@pytest.fixture
def sample_list():
    return [1, 2, 3]

def test_list_length(sample_list):
    assert len(sample_list) == 3
```

When you create a fixture in `pytest`, you can control how often it runs by specifying a scope. This allows you to optimize performance and avoid unnecessary setup/teardown.

Here are the four available fixture scopes:

| Scope      | Runs...                              | Example Use Case                                      |
| ---------- | ------------------------------------ | ----------------------------------------------------- |
| `function` | **Once per test function** (default) | Use for small, fresh setup like a list or a mock      |
| `class`    | Once per **test class**              | Share DB connection or config across tests in a class |
| `module`   | Once per **test file**               | Reuse expensive setup like an API client              |
| `session`  | Once per **entire test run**         | Set up global state like a test database              |

**Example: Fixture with module Scope:**
```python
import pytest

@pytest.fixture(scope="module")
def db_connection():
    print("Connecting to DB...")
    yield "db-conn"
    print("Closing DB connection")

def test_query_1(db_connection):
    assert db_connection == "db-conn"

def test_query_2(db_connection):
    assert isinstance(db_connection, str)
```

In this case, the connection message will print only once for the entire module, and the same `db_connection` value is reused across both tests.

### Categorizing Tests with @pytest.mark
Use `@pytest.mark` to group, tag, or filter tests.

**Example: Marking Tests**
```python
import pytest

@pytest.mark.slow
def test_heavy_computation():
    assert sum(range(1000000)) > 0

@pytest.mark.database
def test_query():
    assert True
```

**Run only marked tests:**
```python
pytest -m slow
```

You can also skip or expect failure:
```python
@pytest.mark.skip(reason="Not implemented yet")
def test_unfinished():
    pass

@pytest.mark.xfail(reason="Known bug")
def test_known_issue():
    assert 1 == 2
```

### Parameterizing Tests
You can test multiple input combinations using `@pytest.mark.parametrize`

```python
import pytest

@pytest.mark.parametrize("a, b, expected", [
    (2, 3, 5),
    (0, 0, 0),
    (-1, 1, 0),
])
def test_add(a, b, expected):
    assert a + b == expected
```

This avoids writing separate test functions for each input set.

To get all combinations of multiple parametrized arguments you can stack parametrize decorators:

```python
import pytest


@pytest.mark.parametrize("x", [0, 1])
@pytest.mark.parametrize("y", [2, 3])
def test_foo(x, y):
    pass
```

This will run the test with the arguments set to `x=0, y=2`, `x=1, y=2`, `x=0, y=3`, and `x=1, y=3` exhausting parameters in the order of the decorators.

## Code Coverage with `pytest-cov`
To see how much of your code is exercised by your tests, use `pytest-cov` to generate a test coverage report.
You can do this by using certain command line options when running `pytest`.

```bash
pytest --cov=my_package --cov-report=html
```

* `--cov`: This specifies the directory for which code testing coverage should evaluated. It tells pytest "look here to see if the tests written cover all the functionality in this directory"
* `--cov-report`: Sets the output format of the coverage report.

If you're using a repository setup with [cookiecutter-cf](https://github.com/carnall-farrar/cookiecutter-cf), these options are already configured in the `pyproject.toml`.

Then open the generated `htmlcov/index.html` in your browser to see the report.
The report tells you how much of your code is being tested. As good practice, you want your coverage to be at least 85%.


## Resources
* [pytest Documentation](https://docs.pytest.org/en/stable/index.html)
* [RealPython - Mocking](https://realpython.com/python-mock-library/)
* [mock.patch decorator - How it works](https://medium.com/uckey/how-mock-patch-decorator-works-in-python-37acd8b78ae)
* [pytest-cov Documentation](https://pytest-cov.readthedocs.io/en/latest/readme.html#usage)