# 📜 Pytest Basics Cheat Sheet

A quick reference for writing and running unit tests in Python using **pytest**.

---

## Installation

```bash
pip install pytest
```

---

## Project Structure Example

```
your_project/
├── my_module.py
└── tests/
    └── test_my_module.py
```

### ✅ Convention:

Test files: test\_\*.py

Test functions: test\_\*

---

## Writing Your First Test

```python
from my_module import add

def test_add():
    assert add(2, 3) == 5

```

✅ Use assert to check results.

---

## Running Tests

From the project root, run in the terminal:

```bash
pytest
```

Pytest will automatically find all files starting with **_test_** and run all functions starting with **_test_**.

---

## Checking Exceptions

```python
import pytest
from my_module import divide

def test_divide_by_zero():
    with pytest.raises(ZeroDivisionError):
        divide(1, 0)
```

Use pytest.raises to test for errors.

---

## Parametrized Tests

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

## Using Fixtures

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

## Checking Prints
You can check if a block of code prints a specific info to the console:

```python
def open_file(capsys):
    print("No such file")

    captured = capsys.readouterr()
    assert "No such file" in captured.out
```

---

## Advanced (Optional) Commands

- Run with detailed output:
  ```bash
  pytest -v
  ```
- Show print output:
  ```bash
  pytest -s
  ```
- Only run tests in a specific file
  ```bash
  pytest tests/test_my_module.py
  ```

---

## Tips & Best Practices

- Name test files **test\_\*.py**
- Name test functions **test\_\***
- Keep tests small and focused.
- Use fixtures for shared setup.
- Use parametrize to avoid duplicate code.
- Use asserts clearly to explain expectations.

---

[Official Pytest Documentation](https://docs.pytest.org/en/stable/)
