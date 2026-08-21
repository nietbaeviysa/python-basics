# Module 15: Python Modules, Namespaces & Script Entry Points

##  Overview
This module explores Python modular design patterns, standard library imports (`math`, `datetime`), and namespace management. It details how to construct clean module namespaces and protect execution flows using the standard `if __name__ == "__main__":` entry point pattern.

##  Key Concepts Covered
* **`import` Statements:** Importing built-in standard library modules (`math`, `datetime`) to leverage pre-built algorithms.
* **`from module import object`:** Selective namespace importing to streamline function and class calls.
* **Static Utility Methods (`@staticmethod`):** Packaging stateless analytical helper functions into logical class structures.
* **Entry Guard (`if __name__ == "__main__":`):** Preventing execution side-effects when importing Python scripts as modules across larger projects.

##  Code Implementation

```python
import math
from datetime import datetime

class AnalyticsEngine:
    @staticmethod
    def calculate_std_dev(scores):
        mean = sum(scores) / len(scores)
        variance = sum((x - mean) ** 2 for x in scores) / len(scores)
        return math.sqrt(variance)

def main():
    data = [85, 92, 78, 95, 88]
    print("Std Dev:", round(AnalyticsEngine.calculate_std_dev(data), 2))

if __name__ == "__main__":
    main()
