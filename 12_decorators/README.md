# Module 12: Python Decorators & Function Wrappers

##  Overview
This module explores Python Decorators and the `@` syntactic sugar. Decorators allow developers to extend or modify the runtime behavior of callable functions dynamically—such as measuring execution benchmarks or adding logging mechanisms—without altering their internal source code.

##  Key Concepts Covered
* **Higher-Order Functions:** Passing functions as arguments and returning wrapped inner functions.
* **Decorator Syntax (`@decorator_name`):** Applying wrapper logic cleanly above target function declarations.
* **`functools.wraps`:** Preserving original function metadata (name, docstrings) inside wrapper scopes.
* **Execution Logging & Benchmarking:** Intercepting function execution to record timing metrics.

##  Code Implementation

```python
import time
import functools

# Decorator definition
def execution_logger(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        print(f"[LOG] Executing '{func.__name__}'")
        result = func(*args, **kwargs)
        print(f"[LOG] Completed in {(time.time() - start)*1000:.2f} ms")
        return result
    return wrapper

# Decorator application
@execution_logger
def process_data(items):
    return [x * 2 for x in items]

# Execution
output = process_data([10, 20, 30])
