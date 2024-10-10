# Python Interview Topics

## Basic Python Concepts

### 1. What are Python's key features?
Python is a versatile, high-level programming language with several key features:
- **Interpreted**: Python code is executed line by line by the Python interpreter at runtime. 
  There's no need for a compilation step before running the code (though Python does create intermediate bytecode for optimization purposes), making it easier to test and debug.
  - Write code → 2. Run the code with the interpreter (e.g., python script.py).
- **Dynamically Typed**: Variables in Python don't need an explicit declaration of their type, but typically resulting in slower performance than compiled languages, (c++, c, java).
- **Object-Oriented**: Python supports classes and objects for encapsulating data and methods.
- **Extensive Libraries**: Python offers rich libraries for various domains like web development, data science, etc.
- **Cross-Platform**: Python programs can run on different platforms without modification.
- **Easy-to-Read Syntax**: Python's code is clean and resembles English, making it beginner-friendly.
- **Indentation**: Python uses indentation to define code blocks, enhancing readability.
- 
### 3. What is the difference between list, tuple, set, and dictionary in Python?

| Data Type   | Ordered | Mutable | Allows Duplicates | Indexed | Syntax |
|-------------|---------|---------|-------------------|---------|--------|
| **List**    | Yes     | Yes     | Yes               | Yes     | `[ ]`  |
| **Tuple**   | Yes     | No      | Yes               | Yes     | `( )`  |
| **Set**     | No      | Yes     | No                | No      | `{ }`  |
| **Dictionary** | No  | Yes     | Keys: No, Values: Yes | Yes | `{key: value}` |

- **List**: A dynamic array; you can add or remove items.
- **Tuple**: Immutable sequence, used for fixed data.
- **Set**: Unordered collection of unique items.
- **Dictionary**: Stores key-value pairs, useful for mapping data.

### 4. What is the purpose of `self` in a Python class?
The `self` keyword refers to the **current instance** of the class. It is used to access the attributes and methods of the class in Python. It must be the first parameter of any method in the class.

```python
class MyClass:
    def __init__(self, name):
        self.name = name

    def greet(self):
        return f"Hello, {self.name}"

obj = MyClass("Atish")
print(obj.greet())  # Output: Hello, Atish
```

### 5. How to Iterate Over a Dictionary in Python

There are several ways to iterate over a dictionary in Python. Below are some common methods:

#### 1. Iterating over dictionary keys
You can iterate through the keys of a dictionary using a simple `for` loop.

```python
my_dict = {'a': 1, 'b': 2, 'c': 3}
```

```python
for key in my_dict:
    print(key)

# Output: a, b, c
```

#### 2. Iterating over dictionary values
You can iterate through the values of a dictionary using the `values()` method.

```python

for value in my_dict.values():
    print(value)
# Output: 1, 2, 3
``` 

#### 3. Iterating over dictionary items
You can iterate through the key-value pairs of a dictionary using the `items()` method.

```python
for key, value in my_dict.items():
    print(key, value)

# Output: a 1, b 2, c 3
``` 

### 6. What is the difference between shallow copy and deep copy?

- **Shallow Copy**: Creates a new object but does not copy nested objects (only references them).
- **Deep Copy**: Recursively copies all objects, creating new instances of every object it references.

#### Example:

```python
import copy

list1 = [[1, 2], [3, 4]]
shallow = copy.copy(list1)
deep = copy.deepcopy(list1)

list1[0][0] = 99
print(shallow)  # Output: [[99, 2], [3, 4]] (reflects changes)
print(deep)     # Output: [[1, 2], [3, 4]] (no change)
```

#### Explanation:
  - In a shallow copy, changes to the original nested objects (like list1[0][0]) will be reflected in the copied object.
  - In a deep copy, the copied object is entirely independent of the original, so changes to the original do not affect the copy.

### 7. Explain the difference between Python's `is` operator and `==` operator.

- **`==`** checks **value equality** (whether the objects have the same value).
- **`is`** checks **identity** (whether they refer to the same object in memory).

#### Example:

```python
a = [1, 2]
b = [1, 2]
print(a == b)  # True (same values)
print(a is b)  # False (different objects)
```

#### Explanation:
  - The `==` operator compares the values of the objects, returning `True` if they are equal.
  - The `is` operator compares the memory addresses of the objects, returning `True` if they point to the same memory location.

### 8. How do you handle exceptions in Python, and how does `try-except-finally` work?

Exceptions in Python are handled using `try`, `except`, and `finally` blocks. The `try` block contains the code that may raise an exception. The `except` block handles the exception, and the `finally` block runs regardless of whether an exception occurs.

#### Example:

```python
try:
    # Code that may raise an exception
    result = 10 / 0
except ZeroDivisionError:
    # Handling the exception
    print("Cannot divide by zero")
finally:
    # Runs no matter what
    print("End of operation")
```
#### Explanation:
  - The `try` block contains the code that may raise an exception.
  - The `except` block catches and handles the exception (e.g., `ZeroDivisionError`).
  - The `finally` block runs regardless of whether an exception occurs, useful for cleanup operations.

### 9. What are context managers in Python, and how do you implement one using the `with` statement?

Context managers allow you to allocate and release resources properly. They are commonly used for file handling or managing connections. The `with` statement ensures that resources are properly cleaned up after use.

#### Example:

```python
class MyContext:
    def __enter__(self):
        print("Entering")
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        print("Exiting")

with MyContext():
    print("Inside the block")
```
#### Explanation:
  - The `__enter__` method sets up the context and returns the resource.
  - The `__exit__` method cleans up the context and handles any exceptions that occur.
  - The `with` statement automatically calls `__enter__` and `__exit__`, ensuring proper resource management.

## Practical Coding Challenges

### 1. Write a function to check if a string is a palindrome.

```python
def is_palindrome(s):
    return s == s[::-1]

print(is_palindrome("radar"))  # True
```

### 2. Write a function to find the factorial of a number using recursion.

```python
def factorial(n):
    return 1 if n == 0 else n * factorial(n - 1)

print(factorial(5))  # 120
 ```

### 3. Write a Python function to merge two dictionaries.

```python
def merge_dicts(dict1, dict2):
    return {**dict1, **dict2}

print(merge_dicts({'a': 1}, {'b': 2}))  # {'a': 1, 'b': 2}
```

### 4. Write a Python function to remove duplicates from a list.

```python 
def remove_duplicates(lst):
    return list(set(lst))
print(remove_duplicates([1, 2, 3, 3, 4]))  # [1, 2, 3, 4]
```

### 5. Write a Python function to sort a list of tuples by the second item.

```python
def sort_tuples(lst):
    return sorted(lst, key=lambda x: x[1])
 print(sort_tuples([(1, 2), (3, 1), (5, 3)]))  # [(3, 1), (1, 2), (5, 3)]

```
### 6. Write a Python function to find the maximum occurring character in a string.

```python
def max_char(s):
    return max(s, key=s.count)
print(max_char("hello"))  # 'l'
```

### 7. Write a Python function to check if a number is prime.

```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True
print(is_prime(11))  # True
```

### 8. Write a Python function to find the intersection of two lists.

```python
def intersection(lst1, lst2):
    return list(set(lst1) & set(lst2))
print(intersection([1, 2, 3], [2, 3, 4]))  # [2, 3]
```

### 9. Write a Python function to reverse a string without using slicing.

```python
def reverse_string(s):
    return "".join(reversed(s))
print(reverse_string("hello"))  # 'olleh'
```

### 10. Write a Python function to merge a list of dictionaries.

```python
def merge_dicts(dicts):
    return {k: v for d in dicts for k, v in d.items()}

print(merge_dicts([{'a': 1}, {'b': 2}]))  # {'a': 1, 'b': 2}

```

### 11. Write a Python function to find the second largest number in a list.

```python
def second_largest(lst):
    return sorted(set(lst))[-2]
print(second_largest([1, 2, 3, 4]))  # 3
```

### 12. Write a Python function to merge two dictionaries.

```python
def merge_dicts(dict1, dict2):
    return {**dict1, **dict2}
print(merge_dicts({'a': 1}, {'b': 2}))  # {'a': 1, 'b': 2}
```

### 13. Write a Python function to merge two dictionaries and add values for common keys.

```python
def merge_dicts(dict1, dict2):
    for key in dict1:
        if key in dict2:
            dict1[key] += dict2[key]
    return {**dict1, **dict2}
print(merge_dicts({'a': 1, 'b': 2}, {'b': 3, 'c': 4}))  # {'a': 1, 'b': 5, 'c': 4}
```

### 14. Write a Python function to find the missing number in a list of numbers.

```python
def find_missing(lst):
    n = len(lst) + 1
    total = n * (n + 1) // 2
    return total - sum(lst)
    
print(find_missing([1, 2, 4, 6, 3, 7, 8]))  # 5

```
### 15. write a Python function to find the tuple exist in the list of tuples.

```python
def find_tuple(lst, tpl):
    return tpl in lst

print(find_tuple([(1, 2), (3, 4), (5, 6)], (3, 4)))  # True

```
