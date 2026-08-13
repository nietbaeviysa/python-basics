# Module 07: Flexible Function Arguments (*args and **kwargs)

##  Overview
This module covers advanced parameter handling in Python functions using variable-length arguments (`*args` and `**kwargs`). Understanding flexible signatures allows developers to write highly adaptable functions capable of processing arbitrary sequences of positional values and key-value metadata dynamically.

##  Key Concepts Covered
* **Positional Arguments Collector (`*args`):** Captures an arbitrary number of positional arguments into a tuple, ideal for variable aggregation (e.g., calculating statistical metrics).
* **Keyword Arguments Collector (`**kwargs`):** Captures arbitrary keyword pairs into a dictionary, enabling flexible object and profile generation.
* **Tuple and Dictionary Iteration:** Extracting values from dynamic argument structures efficiently inside function scopes.

##  Code Implementation

```python
# 1. Flexible positional aggregator
def calculate_average_score(*scores):
    """Calculates average from an arbitrary quantity of numbers."""
    return sum(scores) / len(scores) if scores else 0

# 2. Flexible keyword profile builder
def build_student_profile(name, **metadata):
    """Constructs a dictionary with fixed name and flexible attributes."""
    profile = {"Name": name}
    profile.update(metadata)
    return profile

# Executing functions with dynamic arguments
avg = calculate_average_score(70, 88, 92, 60, 95)
profile = build_student_profile("Iysa", age=19, city="Tashkent", status="Active")

print("Calculated Average:", avg)
print("Generated Profile:", profile)
