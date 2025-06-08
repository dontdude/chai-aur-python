# 🐍 Python Loops for C++ Developers

## 🔁 Python `for` loop vs C++ `for` loop

In C++, a `for` loop has 3 parts:
```cpp
for (int i = 0; i < 5; i++) {
    // do something
}
```

But in Python:
```python
for i in range(5):
    # do something
```

Python's `for` is more like a "for-each" over an iterable (e.g. `range`, list, string, etc.).

---

## 📦 The `range()` Function

`range()` generates a sequence of numbers.

```python
range(stop)              # from 0 to stop-1
range(start, stop)       # from start to stop-1
range(start, stop, step) # custom increment (or decrement)
```

### Examples:
```python
range(5)              # 0, 1, 2, 3, 4
range(2, 5)           # 2, 3, 4
range(10, 2, -2)      # 10, 8, 6, 4
```

Equivalent C++:
```cpp
for (int i = 10; i > 2; i -= 2)
```

---

## ✅ Typical Loop Conversion Examples

### ➤ 1. Count Up

C++:
```cpp
for (int i = 0; i < 5; i++)
```

Python:
```python
for i in range(5):
```

---

### ➤ 2. Count Down

C++:
```cpp
for (int i = 5; i > 0; i--)
```

Python:
```python
for i in range(5, 0, -1):
```

---

### ➤ 3. Custom Steps

C++:
```cpp
for (int i = 2; i <= 10; i += 2)
```

Python:
```python
for i in range(2, 11, 2):
```

---

### ➤ 4. Skip Iteration (`continue`)

C++:
```cpp
for (int i = 0; i < 5; i++) {
    if (i == 2) continue;
}
```

Python:
```python
for i in range(5):
    if i == 2:
        continue
```

---

### ➤ 5. Break Loop

C++:
```cpp
for (int i = 0; i < 10; i++) {
    if (i == 5) break;
}
```

Python:
```python
for i in range(10):
    if i == 5:
        break
```

---

## 🔄 Python `while` Loop

Works just like C++.

C++:
```cpp
int i = 0;
while (i < 5) {
    i++;
}
```

Python:
```python
i = 0
while i < 5:
    i += 1
```

---

## ⚠️ Key Differences & Gotchas

### 🚫 No `i++` or `i--` in Python
Python does not support `++` or `--`.

Use:
```python
i += 1  # instead of i++
i -= 1  # instead of i--
```

---

### 🧠 No 3-part `for` loop in Python

You **must** manage updates inside the body.

C++:
```cpp
for (int i = 2; i <= 100; i *= 3)
```

Python:
```python
i = 2
while i <= 100:
    print(i)
    i *= 3
```

---

### 🔄 Infinite Loop

C++:
```cpp
for (;;) { /* infinite */ }
```

Python:
```python
while True:
    # infinite
```

---

### 😬 Tricky Edge Case: Manual Iterator Manipulation

C++:
```cpp
for (int i = 0; i < 10; ) {
    if (i % 2 == 0)
        i += 2;
    else
        i += 1;
}
```

Python:
```python
i = 0
while i < 10:
    if i % 2 == 0:
        i += 2
    else:
        i += 1
```

---

## 🎯 Looping Over Lists, Strings, etc.

Python supports `for-each` style:

```python
for ch in "hello":
    print(ch)

for item in [10, 20, 30]:
    print(item)
```

C++ equivalent using `range-based for`:
```cpp
for (char ch : "hello") { }
for (auto item : vec) { }
```

---

## 🧹 Summary

| Concept                     | C++                         | Python                       |
|-----------------------------|-----------------------------|------------------------------|
| Count-up loop               | `for (int i = 0; i < n; i++)` | `for i in range(n)`          |
| Count-down loop             | `for (int i = n; i > 0; i--)` | `for i in range(n, 0, -1)`   |
| Infinite loop               | `for (;;)` or `while(true)`  | `while True:`                |
| Skip iteration              | `continue`                   | `continue`                   |
| Break loop                  | `break`                      | `break`                      |
| Custom update (i *= 3, etc) | update in header             | update inside body (use `while`) |
| For-each over collection    | `for (auto x : container)`   | `for x in iterable:`         |

---

Feel free to copy, tweak, or save this file for quick revision!
