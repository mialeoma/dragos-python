# 2️⃣ ADVANCED CONTROLLERS
## Error Handling, Modules, Packages & Advanced Concepts

---

## 📚 What You'll Learn

- **Error Handling** - Try/Except blocks
- **Modules & Imports** - Reuse code
- **File Handling** - Read and write files
- **Debugging** - Find and fix errors
- **Best Practices** - Write clean code

---

## ⚠️ Error Handling (Try/Except)

### Why Error Handling?

Programs crash when errors occur. Error handling lets your program survive!

```python
# WITHOUT error handling (crashes if input is not a number)
age = int(input("Enter your age: "))

# WITH error handling (handles the error gracefully)
try:
    age = int(input("Enter your age: "))
    print(f"You are {age} years old!")
except ValueError:
    print("❌ Error: Please enter a valid number!")
```

### Try/Except Structure

```python
try:
    # Code that might cause an error
    number = int(input("Enter a number: "))
    result = 10 / number
    print(f"10 divided by {number} is {result}")

except ZeroDivisionError:
    # Handle division by zero
    print("❌ Error: Cannot divide by zero!")

except ValueError:
    # Handle invalid input
    print("❌ Error: Please enter a valid number!")

except Exception as e:
    # Handle any other error
    print(f"❌ An error occurred: {e}")

else:
    # This runs if NO error occurred
    print("✅ Success!")

finally:
    # This ALWAYS runs, whether there's an error or not
    print("Program complete!")
```

### Common Errors

| Error | Cause | Example |
|-------|-------|---------|
| **ValueError** | Wrong data type | `int("hello")` |
| **ZeroDivisionError** | Divide by zero | `10 / 0` |
| **IndexError** | Index out of range | `list[10]` when list has 5 items |
| **KeyError** | Dictionary key not found | `dict["missing_key"]` |
| **FileNotFoundError** | File doesn't exist | `open("missing.txt")` |
| **TypeError** | Wrong type for operation | `"hello" + 5` |

---

## 📦 Modules & Imports

### Built-in Modules

```python
# Import the entire module
import math
print(math.pi)        # Output: 3.14159...
print(math.sqrt(16))  # Output: 4.0

# Import specific items
from math import pi, sqrt
print(pi)             # Output: 3.14159...
print(sqrt(25))       # Output: 5.0

# Import with alias
import math as m
print(m.ceil(3.2))    # Output: 4

# Import everything (not recommended)
from math import *
print(sqrt(9))        # Output: 3.0
```

### Useful Built-in Modules

```python
# Random module
import random
print(random.randint(1, 10))      # Random number 1-10
print(random.choice([1, 2, 3]))   # Random from list
print(random.shuffle([1, 2, 3]))  # Shuffle list

# Datetime module
from datetime import datetime, timedelta
now = datetime.now()
print(now)                         # Current date and time
tomorrow = now + timedelta(days=1)
print(tomorrow)                    # Tomorrow's date

# OS module
import os
print(os.getcwd())                # Current working directory
print(os.listdir())               # List files in directory

# Time module
import time
print(time.time())                # Seconds since 1970
time.sleep(2)                     # Wait 2 seconds
```

---

## 📄 File Handling

### Reading Files

```python
# Read entire file
with open("example.txt", "r") as file:
    content = file.read()
    print(content)

# Read line by line
with open("example.txt", "r") as file:
    for line in file:
        print(line.strip())

# Read all lines into a list
with open("example.txt", "r") as file:
    lines = file.readlines()
    print(lines[0])  # First line
```

### Writing Files

```python
# Write to file (overwrites if exists)
with open("output.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("Welcome to Python!")

# Append to file
with open("output.txt", "a") as file:
    file.write("\nAdditional line")

# Write multiple lines
lines = ["Line 1\n", "Line 2\n", "Line 3\n"]
with open("output.txt", "w") as file:
    file.writelines(lines)
```

### File Modes

| Mode | Description |
|------|-------------|
| `r` | Read (default) |
| `w` | Write (overwrites) |
| `a` | Append (add to end) |
| `x` | Create new file |
| `rb` | Read binary |
| `wb` | Write binary |

---

## 🐛 Debugging Techniques

### Print Debugging

```python
def calculate_total(items):
    print(f"DEBUG: items = {items}")  # Check input
    total = 0
    for item in items:
        print(f"DEBUG: Adding {item}, total = {total}")
        total += item
    print(f"DEBUG: Final total = {total}")  # Check output
    return total

result = calculate_total([10, 20, 30])
```

### Using `assert`

```python
def divide(a, b):
    assert b != 0, "Cannot divide by zero!"
    return a / b

result = divide(10, 2)  # Works: 5.0
result = divide(10, 0)  # Fails with AssertionError
```

---

## 💻 Complete Example: Password Manager

```python
# 🐉 DRAGOS PYTHON - Advanced Controllers Demo

import os
import json
from datetime import datetime

def save_password(filename, username, password):
    """Save password to file"""
    try:
        # Load existing passwords
        if os.path.exists(filename):
            with open(filename, "r") as f:
                data = json.load(f)
        else:
            data = {}
        
        # Add new password
        data[username] = {
            "password": password,
            "created": datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        }
        
        # Save to file
        with open(filename, "w") as f:
            json.dump(data, f, indent=4)
        
        print(f"✅ Password saved for {username}")
    
    except Exception as e:
        print(f"❌ Error saving password: {e}")

def load_password(filename, username):
    """Load password from file"""
    try:
        if not os.path.exists(filename):
            print("❌ Password file not found!")
            return None
        
        with open(filename, "r") as f:
            data = json.load(f)
        
        if username in data:
            return data[username]["password"]
        else:
            print(f"❌ No password found for {username}")
            return None
    
    except Exception as e:
        print(f"❌ Error loading password: {e}")
        return None

# Usage
if __name__ == "__main__":
    print("╔════════════════════════════════════╗")
    print("║  DRAGOS PYTHON - Password Manager  ║")
    print("╚════════════════════════════════════╝\n")
    
    save_password("passwords.json", "dragon", "SecurePass123")
    save_password("passwords.json", "user2", "AnotherPass456")
    
    password = load_password("passwords.json", "dragon")
    print(f"Retrieved password: {password}")
```

---

## 🎮 Try It Yourself!

**Challenge 1: Safe Calculator**
```python
# Create a calculator that handles errors
try:
    num1 = float(input("Enter first number: "))
    num2 = float(input("Enter second number: "))
    operation = input("Enter operation (+, -, *, /): ")
    
    if operation == "+":
        print(f"Result: {num1 + num2}")
    elif operation == "/":
        print(f"Result: {num1 / num2}")
    # Add more operations...
except ValueError:
    print("❌ Please enter valid numbers!")
except ZeroDivisionError:
    print("❌ Cannot divide by zero!")
```

**Challenge 2: File Writer**
```python
# Write user input to a file
try:
    filename = input("Enter filename: ")
    with open(filename, "w") as file:
        while True:
            line = input("Enter text (or 'quit' to exit): ")
            if line.lower() == "quit":
                break
            file.write(line + "\n")
    print(f"✅ File '{filename}' saved!")
except Exception as e:
    print(f"❌ Error: {e}")
```

---

## 🔍 Key Takeaways

✅ Use try/except to handle errors gracefully  
✅ Import modules to use pre-written code  
✅ Use `with` statement for safe file handling  
✅ Debug using print statements and assert  
✅ Follow best practices for clean code  

---

<div align="center">

**[← BACK](01-basics.md)** | **[↑ EXIT](../README.md)** | **[▶️ PLAY NOW](03-functions.md)**

</div>
