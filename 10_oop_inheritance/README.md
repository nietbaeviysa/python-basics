# Module 10: OOP Inheritance & Method Overriding

##  Overview
This module explores advanced Object-Oriented Programming (OOP) principles, focusing on Class Inheritance and Method Overriding in Python. Inheritance promotes code reusability by allowing derived child classes to reuse parent behaviors while introducing specialized attributes and logic.

##  Key Concepts Covered
* **Class Inheritance (`class Child(Parent):`):** Extending existing class architectures to build specialized object types.
* **`super()` Function:** Delegate constructor initialization to the parent class to avoid redundant attribute definitions.
* **Method Overriding:** Redefining inherited methods in child classes to implement custom, specialized business rules.

##  Code Implementation

```python
# Parent Class
class Student:
    def __init__(self, name, city):
        self.name = name
        self.city = city
        self.scores = []

    def add_score(self, score):
        self.scores.append(score)

    def get_average(self):
        return sum(self.scores) / len(self.scores) if self.scores else 0.0

# Child Class inheriting from Student
class GraduateStudent(Student):
    def __init__(self, name, city, research_topic):
        super().__init__(name, city)
        self.research_topic = research_topic

    def get_status(self):
        return "Honors" if self.get_average() >= 85 else "Standard Pass"

# Usage
grad = GraduateStudent("Iysa", "Tashkent", "Data Engineering")
grad.add_score(90)
grad.add_score(92)

print(f"{grad.name} | Topic: {grad.research_topic} | Status: {grad.get_status()}")
