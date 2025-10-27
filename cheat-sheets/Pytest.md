# 📜 Pytest Cheatsheet

A quick reference for writing and running unit tests in Python using **pytest**.
[Official Pytest Documentation](https://docs.pytest.org/en/stable/)

---

```bash
pip install pytest                # Install Pytest framework
```

#### Project Structure Example

```bash
my_project/
├── my_module.py
└── tests/
    └── test_my_module.py
```

#### Naming Convention

- Test files: test\_\*.py
- Test functions: test\_\*

#### Commands

To run tests

```bash
pytest -v                         # Show detailed output
pytest -s                         # Show captured print/log output
pytest -q                         # Show less output (Quiet mode)
pytest -v -s                      # Detailed test names and live print output (best for debugging)
pytest -q --tb=short              # Minimal test output with short tracebacks (best for CI)
pytest tests/test_my_module.py    # Only run tests in a specific file
```

---

## Writing Your First Test

```python
from my_module import add

def test_add():
    result = add(2, 3)
    assert result == 5

    # OR with an AssertionError message: assert result == 5, f"add(2,3) returned {result}, expected 5"

```

✅ Use assert to check results.

---

## Running a Test

From the project root, run in the terminal:

```bash
pytest
```

Pytest will automatically find all files starting with **_test_** and run all functions starting with **_test_**.

---

## Checking an Exception

```python
import pytest
from my_module import divide

def test_divide_by_zero():
    with pytest.raises(ZeroDivisionError):
        divide(1, 0)
```

Use pytest.raises to test for errors.

---

## Parametrized Test

Run multiple inputs through the same test:

```python
import pytest
from my_module import add

@pytest.mark.parametrize(
    "a, b, expected",
    [
        (2, 3, 5),
        (-1, 1, 0),
        (0, 0, 0)
    ]
)
def test_add(a, b, expected):
    assert add(a, b) == expected
```

One test function = many cases.

---

## Using Fixture

Fixtures provide setup data for tests:

```python
import pytest

@pytest.fixture
def sample_numbers():
    return (10, 2)

def test_divide(sample_numbers):
    a, b = sample_numbers
    assert a / b == 5
```

Great for preparing data or state.

---

## Expected failure

Tests can be marked as expected to fail and will be grouped as `XFAIL`

```python
import pytest
from my_module import divide

@pytest.mark.xfail(reason="ZeroDivision: attempt to divide by zero")
def test_divide_by_zero(sample_numbers):
    divide(1, 0)
```

---

## Checking Console Print

You can check if a block of code prints a specific info to the console:

```python
def open_file(capsys):
    print("No such file")

    captured = capsys.readouterr()
    assert "No such file" in captured.out
```

---

## Tips & Best Practices

- Name test files **test\_\*.py**
- Name test functions **test\_\***
- Keep tests small and focused.
- Use fixtures for shared setup.
- Use parametrize to avoid duplicate code.
- Use asserts clearly to explain expectations.
