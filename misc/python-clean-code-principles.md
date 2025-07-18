# 🧱 Clean Code Principles

Real-world Python best practices checklist that combines PEP 8, Pythonic principles, and software design standards. You can use this when writing, reviewing, or refactoring code.

---

## 1. Code Style & Structure (PEP 8)

- **_4 spaces_** per indent level (no tabs).
- Max line length: **_79 characters_** (or 88 if using black).
- Imports are grouped: stdlib → third-party → local, with blank lines.
- No wildcard imports (e.g., `from module import \*`).
- Use snake_case for functions and variables.
- Use CamelCase for classes.
- Constants in `ALL_CAPS`.
- One blank line between methods inside a class.
- Two blank lines before top-level functions/classes.
- Use whitespace around operators and after commas.
- Avoid unnecessary parentheses or line breaks.

## 2. Idiomatic Python (Pythonic Code)

- Use **_truthy/falsy_** checks (`if my_list:` not `if len(my_list) > 0:`).
- Use list/set/dict comprehensions instead of loops when appropriate.
- Use `with` statements for file and resource handling.
- Use `enumerate()` instead of manual counters.
- Use tuple unpacking where helpful (`a, b = b, a`).
- Prefer `in` over manual iteration (`if x in list:`).

## 3. Functions & Classes

- Functions do one thing and are short (ideally **_< 50 lines_**).
- Clear function and parameter names.
- Type hints are used where useful: `def func(x: int) -> str`.
- Avoid global variables and mutable default arguments.
- Use `@staticmethod`, `@classmethod`, or `@property` when appropriate.
- Break large classes into smaller, focused ones.
- Use `dataclasses` for simple data containers (Python 3.7+).

## 4. Project Structure & Readability

- Separate concerns into modules: models, views, utils, etc.
- Files are not too long or crowded.
- Avoid long functions, classes, or modules that do too much.
- Use docstrings for all public modules, functions, and classes.
- Avoid deep nesting (**_4+ levels_**).
- Use helper functions for repeated logic.

## 5. Error Handling

- Use `try/except` to catch expected exceptions only.
- Never use a bare except: – always catch specific errors.
- Don't swallow exceptions silently (pass in except is usually bad).
- Use `finally` or context managers to clean up resources.
- Validate inputs and raise appropriate errors (e.g., `ValueError`).

## 6. Clean Code Principles (SOLID & DRY)

- Functions/classes have a single responsibility.
- No copy-paste code; repeated logic is abstracted.
- Prefer composition over inheritance unless inheritance is natural.
- Code is open for extension, closed for modification.
- Abstractions are used to separate layers (e.g., DB access via interface).

## 7. Testing & Type Safety

- All core logic is covered by tests (use `pytest` or `unittest`).
- Avoid hard-to-test code (e.g., tightly coupled functions).
- Use `mypy` or `pyright` for static type checking.
- **_No print-based_** debugging left in production code.
- Add tests for edge cases and error conditions.

## 8. Tooling (Automation & Linting)

- Code is autoformatted with `black` or `ruff` format.
- `flake8`, `pylint`, or `ruff` used to enforce lint rules.
- Type checking passes (`mypy`, `pyright`).
- Tests can be run easily (`pytest`, test runner setup).
- Optional: Pre-commit hooks set up (pre-commit framework).

## 9. Documentation

- Project includes a **README** with install & usage instructions.
- Complex functions/classes are documented with purpose and behavior.
- Public APIs include docstrings.
- Code comments are minimal but useful and up to date.

## 10. Zen of Python (Mental Model)

- Code favors readability over cleverness.
- Prefer simple solutions to complex ones.
- Avoid premature optimization.
- There’s one (preferably obvious) way to do it.
- Don’t reinvent the wheel – use Python’s standard library.
