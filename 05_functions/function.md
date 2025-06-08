# 🐍 Python Functions for C++ Developers

---

## 🔹 1. Defining a Function

### C++ function:

```cpp
int add(int a, int b) {
    return a + b;
}
```

### Python function:

```python
def add(a, b):
    return a + b
```

- No type declarations needed in Python.
- Use `def` keyword.
- Indentation defines the function body (no `{}`).
- No semicolons `;` at end of lines.

---

## 🔹 2. Calling Functions

Same idea in both languages:

C++:

```cpp
int result = add(2, 3);
```

Python:

```python
result = add(2, 3)
```

---

## 🔹 3. Function Arguments

### Positional arguments (most common):

Python:

```python
def greet(name, age):
    print(f"Hello {name}, you are {age} years old")

greet("Alice", 25)
```

C++:

```cpp
void greet(string name, int age) {
    cout << "Hello " << name << ", you are " << age << " years old\n";
}

greet("Alice", 25);
```

---

### 🧩 4. Default Arguments

Python:

```python
def greet(name="User", age=30):
    print(f"Hello {name}, you are {age} years old")

greet()              # uses default values
greet("Bob")         # age uses default
greet("Charlie", 40) # overrides both
```

C++:

```cpp
void greet(string name = "User", int age = 30) {
    cout << "Hello " << name << ", you are " << age << " years old\n";
}

greet();
greet("Bob");
greet("Charlie", 40);
```

---

### 🧩 5. Keyword Arguments (Python-only)

You can call functions specifying argument names:

```python
greet(age=45, name="Diana")
```

No direct equivalent in C++ (except with some template magic or structs).

---

## 🔹 6. Return Values

Functions can return anything, including multiple values.

### Single return:

Python:

```python
def square(x):
    return x * x
```

C++:

```cpp
int square(int x) {
    return x * x;
}
```

### Multiple returns in Python:

```python
def get_min_max(numbers):
    return min(numbers), max(numbers)

min_val, max_val = get_min_max([3, 7, 1, 9])
```

No direct multiple return in C++ (usually use `std::pair` or structs).

---

## 🔹 7. No Function Overloading in Python

In C++, you can have multiple functions with the same name but different parameters:

```cpp
int add(int a, int b);
double add(double a, double b);
```

Python does **not** support this directly — redefining a function replaces the old one.

---

## 🔹 8. Variable Number of Arguments (`*args`, `**kwargs`)

Python supports flexible arguments:

```python
def foo(*args, **kwargs):
    print("Positional:", args)
    print("Keyword:", kwargs)

foo(1, 2, a=3, b=4)
```

- `*args` collects extra positional args as a tuple.
- `**kwargs` collects extra named args as a dict.

No direct equivalent in simple C++, but you can do variadic templates or ellipsis `...`.

---

## 🔹 9. Anonymous Functions (Lambdas)

Python:

```python
square = lambda x: x * x
print(square(5))  # prints 25
```

C++ (since C++11):

```cpp
auto square = [](int x) { return x * x; };
cout << square(5) << endl;
```

---

## 🔹 10. Functions Are First-Class Objects

Python functions can be assigned to variables, passed around:

```python
def shout(text):
    return text.upper()

func = shout
print(func("hello"))
```

Similar in C++ with function pointers or `std::function`.

---

## 🔹 11. Nested Functions & Closures

Python allows functions inside functions:

```python
def outer(x):
    def inner(y):
        return x + y
    return inner

add_five = outer(5)
print(add_five(10))  # 15
```

---

## 🔹 12. Docstrings (Function Documentation)

Python supports inline docs:

```python
def add(a, b):
    """Return the sum of a and b."""
    return a + b

help(add)
```

---

## 🔹 13. Example: Edge Cases

### No explicit return means function returns `None` in Python:

```python
def foo():
    pass

result = foo()
print(result)  # prints None
```

C++ requires a return if the function expects it.

---

## 🔹 14. Example: Mutable Default Argument Pitfall

```python
def append_to_list(value, my_list=[]):
    my_list.append(value)
    return my_list

print(append_to_list(1))  # [1]
print(append_to_list(2))  # [1, 2] — unexpected!
```

**Why?** Default args are evaluated once, not each call.

**Fix:**

```python
def append_to_list(value, my_list=None):
    if my_list is None:
        my_list = []
    my_list.append(value)
    return my_list
```

---

## 🧹 Summary Table

| Concept                | C++                                    | Python                    |
| ---------------------- | -------------------------------------- | ------------------------- |
| Define function        | `int add(int a, int b)`                | `def add(a, b):`          |
| Default arguments      | Supported                              | Supported                 |
| Function overloading   | Supported                              | Not supported             |
| Multiple return values | Use structs, pairs                     | Return tuple              |
| Variable args          | Variadic templates, ellipsis           | `*args`, `**kwargs`       |
| Anonymous functions    | Lambdas (C++11+)                       | `lambda`                  |
| Nested functions       | Harder, function pointers              | Supported                 |
| Docstrings             | Comments only                          | Supported                 |
| No explicit return     | Compiler error if return type non-void | Returns `None` by default |

---

Feel free to ask if you want me to generate a downloadable `.md` file or provide real-world examples with files, classes, or decorators!
