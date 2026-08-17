# Module 11: Memory-Efficient Data Processing via Generators (`yield`)

##  Overview
This module explores Generators and lazy evaluation in Python using the `yield` statement. Generators enable memory-efficient processing of massive or streaming datasets by producing item elements on demand rather than loading entire collections into RAM at once.

##  Key Concepts Covered
* **`yield` Keyword:** Pausing function execution state and yielding a value to the caller dynamically.
* **Lazy Evaluation:** Computing data elements on-the-fly only when requested by iteration or callers.
* **`next()` Function:** Manually advancing generator execution stream to retrieve the next sequence item.
* **Memory Optimization:** Reducing RAM consumption when parsing large log files or tabular datasets.

##  Code Implementation

```python
raw_logs = ["Iysa,95,Passed", "Alice,82,Passed", "Bob,45,Failed"]

# Generator function definition
def process_logs_generator(logs):
    for record in logs:
        name, score, status = record.split(",")
        yield {"Name": name, "Score": int(score)}

# Consuming generator stream
stream = process_logs_generator(raw_logs)

for entry in stream:
    print(f"Student: {entry['Name']} | Score: {entry['Score']}")
