# 🐍 Object-Oriented Programming (OOP) in Python

### For C++ Developers

---

## 🔹 1. Defining a Class

### C++:

```cpp
class Person {
public:
    string name;
    int age;

    Person(string n, int a) : name(n), age(a) {}

    void greet() {
        cout << "Hello, " << name << endl;
    }
};
```

### Python:

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        print(f"Hello, {self.name}")
```

- `__init__` is the constructor.
- `self` refers to the current instance (similar to `this` in C++).
- No access specifiers (`public`, `private`) by default.

---

## 🔹 2. Creating Objects (Instances)

C++:

```cpp
Person p("Alice", 30);
p.greet();
```

Python:

```python
p = Person("Alice", 30)
p.greet()
```

---

## 🔹 3. Instance Variables vs Class Variables

### Instance variables — unique to each object.

```python
p1 = Person("Alice", 30)
p2 = Person("Bob", 25)
```

### Class variables — shared across all instances.

```python
class Person:
    species = "Homo sapiens"  # class variable

    def __init__(self, name):
        self.name = name

print(Person.species)
print(p1.species)
p1.species = "Alien"
print(p1.species)  # overrides class variable only for p1
print(p2.species)  # remains "Homo sapiens"
```

---

## 🔹 4. Access Specifiers: Public, Private, Protected

Python does not enforce strict access control:

- Public: normal attribute `self.name`
- Protected (convention): prefix with `_` like `_age` (treated as internal)
- Private (name mangling): prefix with `__` like `__salary`

```python
class Employee:
    def __init__(self):
        self.name = "John"        # public
        self._age = 30            # protected (convention)
        self.__salary = 50000     # private (name mangled)

e = Employee()
print(e.name)      # works
print(e._age)      # works but discouraged
print(e.__salary)  # AttributeError

# Access private via name mangling
print(e._Employee__salary)  # works but avoid doing this
```

---

## 🔹 5. Inheritance

### C++:

```cpp
class Animal {
public:
    void speak() { cout << "Animal sound"; }
};

class Dog : public Animal {
public:
    void speak() { cout << "Woof"; }
};
```

### Python:

```python
class Animal:
    def speak(self):
        print("Animal sound")

class Dog(Animal):
    def speak(self):
        print("Woof")
```

---

## 🔹 6. Calling Parent Class Methods

Python uses `super()`:

```python
class Dog(Animal):
    def speak(self):
        super().speak()  # calls Animal's speak
        print("Woof")
```

---

## 🔹 7. Method Overriding & Polymorphism

```python
def animal_speak(animal):
    animal.speak()

dog = Dog()
animal = Animal()

animal_speak(animal)  # Animal sound
animal_speak(dog)     # Woof
```

No explicit interfaces needed for basic polymorphism (duck typing).

---

## 🔹 8. Special Methods (Magic/Dunder Methods)

- `__str__(self)`: string representation (like `toString()` in C++)
- `__repr__(self)`: official string representation
- `__eq__(self, other)`: equality operator override
- `__len__(self)`: length (for `len()`)

Example:

```python
class Person:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"Person named {self.name}"

p = Person("Alice")
print(p)  # Person named Alice
```

---

## 🔹 9. Properties (Getters and Setters)

Python uses `@property` decorator instead of explicit getters/setters:

```python
class Person:
    def __init__(self, age):
        self._age = age

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, value):
        if value < 0:
            raise ValueError("Age cannot be negative")
        self._age = value

p = Person(30)
print(p.age)  # getter called

p.age = 35    # setter called
# p.age = -5  # raises ValueError
```

---

## 🔹 10. Class Methods and Static Methods

- `@classmethod` — receives class (`cls`) as first argument.
- `@staticmethod` — no automatic first argument.

```python
class MyClass:
    count = 0

    @classmethod
    def increment_count(cls):
        cls.count += 1

    @staticmethod
    def greet():
        print("Hello from static method")

MyClass.increment_count()
print(MyClass.count)

MyClass.greet()
```

---

## 🔹 11. Multiple Inheritance

Python supports it (C++ also does):

```python
class Flyer:
    def fly(self):
        print("Flying")

class Swimmer:
    def swim(self):
        print("Swimming")

class Duck(Flyer, Swimmer):
    pass

d = Duck()
d.fly()
d.swim()
```

---

## 🔹 12. Private Variables and Name Mangling

Python “private” variables are name-mangled to avoid accidental access:

```python
class C:
    def __init__(self):
        self.__private = 42

obj = C()
print(obj.__private)       # AttributeError
print(obj._C__private)     # 42 (name mangled)
```

---

## 🔹 13. Summary Table

| Concept              | C++                                 | Python                             |
| -------------------- | ----------------------------------- | ---------------------------------- |
| Class declaration    | `class C { ... };`                  | `class C:`                         |
| Constructor          | `C() { ... }`                       | `def __init__(self):`              |
| Member access        | public/private/protected            | Public by default, convention only |
| Inheritance          | `class D : public B {}`             | `class D(B):`                      |
| Method overriding    | Supported                           | Supported                          |
| Polymorphism         | Via virtual functions, interfaces   | Duck typing, no strict interfaces  |
| Getters/setters      | Explicit functions                  | `@property` decorator              |
| Static methods       | `static` keyword                    | `@staticmethod` decorator          |
| Class methods        | Static + explicit `this` management | `@classmethod` decorator           |
| Multiple inheritance | Supported                           | Supported                          |
| Private variables    | Enforced by compiler                | Name mangling with `__` prefix     |

---

If you want a downloadable `.md` file or specific examples for advanced OOP concepts like metaclasses, decorators, or mixins, just ask!
