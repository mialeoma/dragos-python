# 1️⃣ BASIC CONTROLLERS
## Variables, Data Types, Input/Output

---

## 📚 What You'll Learn

- **Variables** - Store and manage data
- **Data Types** - Strings, Integers, Floats, Booleans
- **Input/Output** - Get user input and display output
- **Basic Operations** - Arithmetic and string operations

---

## 🎯 Variables & Data Types

### What is a Variable?

A variable is a container that stores a value. Think of it as a labeled box!

```python
# Creating variables
name = "Drago"          # String (text)
age = 25                # Integer (whole number)
height = 5.9            # Float (decimal number)
is_learning = True      # Boolean (True/False)

print(name)
print(age)
print(height)
print(is_learning)
```

### Data Types in Python

| Type | Example | Description |
|------|---------|-------------|
| **String** | `"Hello"` | Text data |
| **Integer** | `42` | Whole numbers |
| **Float** | `3.14` | Decimal numbers |
| **Boolean** | `True/False` | True or False values |
| **List** | `[1, 2, 3]` | Collection of items |
| **Dictionary** | `{"name": "Drago"}` | Key-value pairs |

---

## 💬 Input & Output

### Output with `print()`

```python
# Basic print
print("Welcome to Dragos Python!")

# Print multiple items
print("Name:", "Drago", "Age:", 25)

# Print with formatting
name = "Drago"
print(f"Hello, {name}! Welcome!")
```

### Input with `input()`

```python
# Get user input
name = input("What's your name? ")
print(f"Nice to meet you, {name}!")

# Get number input (convert string to integer)
age = int(input("How old are you? "))
print(f"You are {age} years old!")

# Get decimal input
height = float(input("What's your height? "))
print(f"Your height is {height} meters!")
```

---

## 🧮 Basic Operations

### Arithmetic Operations

```python
# Addition
a = 10
b = 5
print(a + b)  # Output: 15

# Subtraction
print(a - b)  # Output: 5

# Multiplication
print(a * b)  # Output: 50

# Division
print(a / b)  # Output: 2.0

# Floor Division (rounds down)
print(a // b)  # Output: 2

# Modulo (remainder)
print(a % b)  # Output: 0

# Exponent (power)
print(a ** 2)  # Output: 100
```

### String Operations

```python
# String concatenation
first_name = "Drago"
last_name = "Python"
full_name = first_name + " " + last_name
print(full_name)  # Output: Drago Python

# String repetition
print("Ha" * 3)  # Output: HaHaHa

# String length
print(len(full_name))  # Output: 12

# String methods
text = "hello"
print(text.upper())      # Output: HELLO
print(text.capitalize()) # Output: Hello
```

---

## 📝 Complete Example Program

```python
# 🐉 DRAGOS PYTHON - Basic Controllers Demo

print("╔════════════════════════════════════╗")
print("║  DRAGOS PYTHON - BASIC CONTROLLERS ║")
print("╚════════════════════════════════════╝\n")

# Get user information
name = input("🎮 What's your name, adventurer? ")
age = int(input("🎂 How old are you? "))
favorite_language = input("💻 What's your favorite programming language? ")

# Display information
print("\n✨ Your Profile:")
print(f"Name: {name}")
print(f"Age: {age}")
print(f"Favorite Language: {favorite_language}")

# Calculate years until 100
years_left = 100 - age
print(f"\n📊 You have {years_left} years until 100!")

# Simple calculation
print(f"\n🧮 In 10 years, you'll be {age + 10} years old!")
```

---

## 🎮 Try It Yourself!

**Challenge 1: Temperature Converter**
```python
# Convert Celsius to Fahrenheit
celsius = float(input("Enter temperature in Celsius: "))
fahrenheit = (celsius * 9/5) + 32
print(f"{celsius}°C = {fahrenheit}°F")
```

**Challenge 2: Area Calculator**
```python
# Calculate area of a rectangle
length = float(input("Enter length: "))
width = float(input("Enter width: "))
area = length * width
print(f"Area: {area} square units")
```

**Challenge 3: Greeting Program**
```python
# Create a personalized greeting
name = input("Your name: ")
age = int(input("Your age: "))
city = input("Your city: ")

print(f"\nHello {name}!")
print(f"You are {age} years old")
print(f"You live in {city}")
print(f"That's wonderful!\n")
```

---

## 🔍 Key Takeaways

✅ Variables store data in labeled containers  
✅ Python has multiple data types (strings, integers, floats, booleans)  
✅ `print()` displays output to the screen  
✅ `input()` gets data from the user  
✅ You can perform operations on numbers and strings  

---

<div align="center">

**[← BACK](#basic-controllers)** | **[↑ EXIT](../README.md)** | **[▶️ PLAY NOW](02-advanced.md)**

</div>
