# 3️⃣ FUNCTIONS & METHODS
## Defining, Calling, Parameters, Return Values & Best Practices

---

## 📚 What You'll Learn

- **Function Basics** - Define and call functions
- **Parameters** - Pass data to functions
- **Return Values** - Get results from functions
- **Scope** - Variable visibility
- **Built-in Functions** - Use Python's ready-made functions

---

## 🎯 Function Basics

### What is a Function?

A function is a reusable block of code that performs a specific task.

```python
# Define a function
def greet():
    print("Hello, adventurer!")
    print("Welcome to Dragos Python!")

# Call the function
greet()
greet()  # You can call it multiple times!
```

### Function Syntax

```python
def function_name(parameters):
    """Docstring - describes what the function does"""
    # Function body - code goes here
    return result  # Optional return statement
```

---

## 📥 Parameters & Arguments

### Single Parameter

```python
def greet(name):
    print(f"Hello, {name}!")

greet("Drago")      # Output: Hello, Drago!
greet("Player")     # Output: Hello, Player!
```

### Multiple Parameters

```python
def add(a, b):
    """Add two numbers together"""
    result = a + b
    return result

sum_result = add(5, 3)
print(sum_result)  # Output: 8
```

### Default Parameters

```python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet("Drago")                      # Output: Hello, Drago!
greet("Drago", "Welcome")           # Output: Welcome, Drago!
greet("Drago", greeting="Greetings") # Output: Greetings, Drago!
```

### Variable Number of Parameters

```python
# *args - accept any number of arguments
def add_all(*numbers):
    total = 0
    for num in numbers:
        total += num
    return total

print(add_all(1, 2, 3))           # Output: 6
print(add_all(1, 2, 3, 4, 5))     # Output: 15

# **kwargs - accept keyword arguments
def print_info(**info):
    for key, value in info.items():
        print(f"{key}: {value}")

print_info(name="Drago", age=25, city="Python City")
# Output:
# name: Drago
# age: 25
# city: Python City
```

---

## 📤 Return Values

### Returning a Single Value

```python
def square(x):
    return x * x

result = square(5)
print(result)  # Output: 25
```

### Returning Multiple Values

```python
def get_coordinates():
    x = 10
    y = 20
    return x, y

x_coord, y_coord = get_coordinates()
print(f"X: {x_coord}, Y: {y_coord}")
# Output: X: 10, Y: 20
```

### Returning Early

```python
def check_age(age):
    if age < 0:
        print("❌ Age cannot be negative!")
        return False
    
    if age < 18:
        print("⚠️ You are a minor")
        return "Minor"
    
    print("✅ You are an adult")
    return "Adult"

print(check_age(-5))   # Output: ❌ Age cannot be negative! | False
print(check_age(15))   # Output: ⚠️ You are a minor | Minor
print(check_age(25))   # Output: ✅ You are an adult | Adult
```

---

## 🔍 Variable Scope

### Local vs Global

```python
# Global variable
global_var = "I'm global"

def my_function():
    # Local variable
    local_var = "I'm local"
    print(local_var)      # Works: I'm local
    print(global_var)     # Works: I'm global

my_function()
print(local_var)         # ERROR: local_var not defined
print(global_var)        # Works: I'm global
```

### Modifying Global Variables

```python
counter = 0

def increment():
    global counter
    counter += 1

print(counter)    # Output: 0
increment()
print(counter)    # Output: 1
increment()
print(counter)    # Output: 2
```

---

## 🏗️ Function Organization

### Docstrings

```python
def calculate_discount(price, discount_percent):
    """
    Calculate the final price after applying a discount.
    
    Args:
        price (float): Original price
        discount_percent (float): Discount percentage (0-100)
    
    Returns:
        float: Final price after discount
    
    Example:
        >>> calculate_discount(100, 20)
        80.0
    """
    discount_amount = price * (discount_percent / 100)
    final_price = price - discount_amount
    return final_price

# Access docstring
print(calculate_discount.__doc__)
```

### Docstring Types

```python
# Single line docstring
def greet(name):
    """Greet someone by name."""
    print(f"Hello, {name}!")

# Multi-line docstring
def complex_function(param1, param2):
    """
    This function does something complex.
    
    Args:
        param1: First parameter
        param2: Second parameter
    
    Returns:
        The result of the operation
    """
    return param1 + param2
```

---

## 🎮 Complete Example: Game Menu System

```python
# 🐉 DRAGOS PYTHON - Functions Demo

def display_menu():
    """Display the main game menu"""
    print("\n╔════════════════════════════════════╗")
    print("║        DRAGOS PYTHON GAME         ║")
    print("╠════════════════════════════════════╣")
    print("║ 1. Start Game                      ║")
    print("║ 2. Settings                        ║")
    print("║ 3. High Scores                     ║")
    print("║ 4. Exit                            ║")
    print("╚════════════════════════════════════╝")

def get_player_choice():
    """Get and validate player choice"""
    while True:
        try:
            choice = int(input("\nEnter your choice (1-4): "))
            if 1 <= choice <= 4:
                return choice
            else:
                print("❌ Please enter a number between 1 and 4!")
        except ValueError:
            print("❌ Please enter a valid number!")

def start_game():
    """Start the game"""
    print("\n🎮 Starting game...")
    print("✨ Adventure awaits!")

def show_settings():
    """Show settings menu"""
    print("\n⚙️ Settings")
    print("- Difficulty: Normal")
    print("- Sound: ON")
    print("- Music: ON")

def show_high_scores():
    """Display high scores"""
    print("\n🏆 High Scores")
    print("1. Dragon Master - 10,000 points")
    print("2. Python Ninja - 8,500 points")
    print("3. Code Wizard - 7,200 points")

def main():
    """Main game loop"""
    print("╔════════════════════════════════════╗")
    print("║  Welcome to DRAGOS PYTHON GAME!    ║")
    print("╚════════════════════════════════════╝")
    
    while True:
        display_menu()
        choice = get_player_choice()
        
        if choice == 1:
            start_game()
        elif choice == 2:
            show_settings()
        elif choice == 3:
            show_high_scores()
        elif choice == 4:
            print("\n👋 Thanks for playing! Goodbye!")
            break

if __name__ == "__main__":
    main()
```

---

## 🎮 Try It Yourself!

**Challenge 1: Math Functions**
```python
def multiply(a, b):
    """Multiply two numbers"""
    return a * b

def power(base, exponent=2):
    """Raise base to power (default is 2)"""
    return base ** exponent

print(multiply(5, 3))      # Output: 15
print(power(5))            # Output: 25
print(power(5, 3))         # Output: 125
```

**Challenge 2: String Functions**
```python
def reverse_string(text):
    """Reverse a string"""
    return text[::-1]

def count_vowels(text):
    """Count vowels in a string"""
    vowels = "aeiouAEIOU"
    count = 0
    for char in text:
        if char in vowels:
            count += 1
    return count

print(reverse_string("Hello"))      # Output: olleH
print(count_vowels("Python"))       # Output: 1
```

**Challenge 3: List Functions**
```python
def find_max(numbers):
    """Find maximum number in list"""
    if not numbers:
        return None
    max_num = numbers[0]
    for num in numbers:
        if num > max_num:
            max_num = num
    return max_num

def average(numbers):
    """Calculate average of numbers"""
    if not numbers:
        return 0
    return sum(numbers) / len(numbers)

print(find_max([5, 2, 8, 1, 9]))    # Output: 9
print(average([10, 20, 30]))        # Output: 20.0
```

---

## 🔍 Key Takeaways

✅ Functions organize code and make it reusable  
✅ Parameters allow you to pass data into functions  
✅ Return values let functions send data back  
✅ Scope determines where variables can be accessed  
✅ Docstrings document what your function does  

---

<div align="center">

**[← BACK](02-advanced.md)** | **[↑ EXIT](../README.md)** | **[▶️ PLAY NOW](04-loops.md)**

</div>
