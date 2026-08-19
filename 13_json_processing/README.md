# Module 13: JSON Data Processing & API Parsing

##  Overview
This module explores processing JavaScript Object Notation (JSON) payloads using Python's native `json` library. Handling nested key-value pairs, parsing API response streams, and converting dictionaries back into formatted JSON payloads are core skill sets in modern Data Engineering pipelines.

##  Key Concepts Covered
* **`json.loads()`:** Deserializing raw JSON strings into native Python dictionaries and lists.
* **`json.dumps()`:** Serializing Python objects into formatted JSON strings with configurable indentations (`indent=4`).
* **Nested Parsing:** Accessing multi-level dictionary keys and array objects cleanly.
* **API Data Extraction:** Extracting key attributes and transforming data streams into aggregated analytics.

##  Code Implementation

```python
import json

raw_json = '{"students": [{"name": "Iysa", "score": 95}, {"name": "Alice", "score": 88}]}'

# Parsing JSON string to Dict
data = json.loads(raw_json)

# Extracting data
top_students = [s["name"] for s in data["students"] if s["score"] >= 90]

# Converting back to JSON
json_output = json.dumps({"top_performers": top_students}, indent=2)
print(json_output)
