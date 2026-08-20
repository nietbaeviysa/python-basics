# Module 14: Robust Error Handling & Custom Exceptions

##  Overview
This module demonstrates defensive programming and fault-tolerant data ingestion patterns in Python. Utilizing structured `try-except-else-finally` blocks along with custom user-defined exceptions prevents application crashes when parsing corrupted, malformed, or out-of-bound data items.

##  Key Concepts Covered
* **`try-except` Blocks:** Intercepting built-in exceptions (`ValueError`) to maintain execution continuity.
* **Custom Exceptions (`class CustomError(Exception)`):** Designing user-defined exceptions to enforce domain-specific validation rules.
* **`else` Clause:** Executing clean control flow logic strictly when no runtime errors occur.
* **`finally` Clause:** Executing cleanup code unconditionally after try-except blocks complete.

##  Code Implementation

```python
class InvalidScoreError(Exception):
    pass

def parse_record(raw_item):
    try:
        name, score_str = raw_item.split(",")
        score = float(score_str)
        if not (0 <= score <= 100):
            raise InvalidScoreError("Score out of bounds")
    except (ValueError, InvalidScoreError) as e:
        print(f"[LOG ERROR] {e}")
        return None
    else:
        return {"Name": name, "Score": score}

# Ingesting clean and corrupted data
print(parse_record("Iysa,95"))
print(parse_record("BadData,150"))
