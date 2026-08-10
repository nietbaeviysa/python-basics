# Module 04: File Handling & Exception Handling in Python

# Overview
This module explores external file I/O operations and error management in Python. Learning to write to and safely read from text files using context managers (`with open`) and exception handlers (`try / except`) is an essential requirement for real-world Data Engineering and Analysis workflows.

# Key Concepts Covered
* **Context Manager (`with open(...) as file:`):** Ensures safe file operations by automatically closing file streams after execution.
* **File Modes:**
  * `"w"` — Write mode (creates a new file or overwrites existing content).
  * `"r"` — Read mode (retrieves file contents).
* **Escape Characters (`\n`):** Formatting multi-line output using newline characters.
* **String Parsing (`.read().splitlines()`):** Reading entire file content and converting lines into a clean Python list without trailing `\n`.
* **Exception Handling (`try / except`):** Intercepting runtime errors (such as `FileNotFoundError`) to prevent application crashes.

# Code Implementation

```python
# Dataset and target path
student_logs = ["Alice: 90", "Bob: 85", "Charlie: 78", "Diana: 92"]
file_path = "journal.txt"

# 1. Writing records to a file
with open(file_path, "w") as file:
    for record in student_logs:
        file.write(record + "\n")

# 2. Safe file reading and parsing
try:
    with open(file_path, "r") as file:
        read_logs = file.read().splitlines()

    print("Successfully loaded records:", read_logs)
    print("Total journal entries:", len(read_logs))

except FileNotFoundError:
    print(f"Error: The file '{file_path}' was not found!")
