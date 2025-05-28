# Object-Oriented-Programming-Assignments

# 1. Using self
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

   def display(self):
        print(f"Name: {self.name}, Marks: {self.marks}")

# 2. Using cls
class Counter:
    count = 0

   def __init__(self):
        Counter.count += 1

   @classmethod
    def display_count(cls):
        print(f"Total objects created: {cls.count}")

# 3. Public Variables and Methods
class Car:
    def __init__(self, brand):
        self.brand = brand

  def start(self):
        print(f"{self.brand} car is starting...")

# 4. Class Variables and Class Methods
class Bank:
    bank_name = "Default Bank"

   @classmethod
    def change_bank_name(cls, name):
        cls.bank_name = name

# 5. Static Variables and Static Methods
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b

# 6. Constructors and Destructors
class Logger:
    def __init__(self):
        print("Logger created")

   def __del__(self):
        print("Logger destroyed")

# 7. Access Modifiers: Public, Private, and Protected
class Employee:
    def __init__(self, name, salary, ssn):
        self.name = name
        self._salary = salary
        self.__ssn = ssn

emp = Employee("John", 50000, "123-45-6789")
print(emp.name)        # public
print(emp._salary)     # protected (accessible, but discouraged)
# print(emp.__ssn)     # private (raises AttributeError)
print(emp._Employee__ssn)  # name mangling workaround

# 8. The super() Function
class Person:
    def __init__(self, name):
        self.name = name

class Teacher(Person):
    def __init__(self, name, subject):
        super().__init__(name)
        self.subject = subject

# 9. Abstract Classes and Methods
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

   def area(self):
        return self.width * self.height

# 10. Instance Methods
class Dog:
    def __init__(self, name, breed):
        self.name = name
        self.breed = breed

   def bark(self):
        print(f"{self.name} says Woof!")

# 11. Class Methods
class Book:
    total_books = 0

  @classmethod
    def increment_book_count(cls):
        cls.total_books += 1

# 12. Static Methods
class TemperatureConverter:
    @staticmethod
    def celsius_to_fahrenheit(c):
        return (c * 9/5) + 32

# 13. Composition
class Engine:
    def start(self):
        print("Engine started")

class Car:
    def __init__(self, engine):
        self.engine = engine

  def start(self):
        self.engine.start()

# 14. Aggregation
class Department:
    def __init__(self, name):
        self.name = name
        self.employees = []

   def add_employee(self, employee):
        self.employees.append(employee)

class Employee:
    def __init__(self, name):
        self.name = name

# 15. Method Resolution Order (MRO) and Diamond Inheritance
class A:
    def show(self):
        print("A")

class B(A):
    def show(self):
        print("B")

class C(A):
    def show(self):
        print("C")

class D(B, C):
    pass

d = D()
d.show()  # MRO will determine if B.show or C.show is used

# 16. Function Decorators
def log_function_call(func):
    def wrapper():
        print("Function is being called")
        return func()
    return wrapper

@log_function_call
def say_hello():
    print("Hello")

# 17. Class Decorators
def add_greeting(cls):
    def greet(self):
        return "Hello from Decorator!"
    cls.greet = greet
    return cls

@add_greeting
class Person:
    pass

# 18. Property Decorators: @property, @setter, and @deleter
class Product:
    def __init__(self, price):
        self._price = price

   @property
    def price(self):
        return self._price

   @price.setter
    def price(self, value):
        self._price = value

  @price.deleter
    def price(self):
        del self._price

# 19. callable() and __call__()
class Multiplier:
    def __init__(self, factor):
        self.factor = factor

   def __call__(self, x):
        return x * self.factor

m = Multiplier(5)
print(callable(m))  # True
print(m(3))         # 15

# 20. Creating a Custom Exception
class InvalidAgeError(Exception):
    pass

def check_age(age):
    if age < 18:
        raise InvalidAgeError("Age must be 18 or older")
    else:
        print("Age is valid")

# 21. Make a Custom Class Iterable
class Countdown:
    def __init__(self, start):
        self.current = start

  def __iter__(self):
        return self

   def __next__(self):
        if self.current < 0:
            raise StopIteration
        value = self.current
        self.current -= 1
        return value
