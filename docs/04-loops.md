# 4️⃣ LOOPS & ITERATIONS
## For Loops, While Loops, Break, Continue & Nested Loops

---

## 📚 What You'll Learn

- **For Loops** - Iterate over sequences
- **While Loops** - Repeat until condition is false
- **Loop Control** - Break and continue statements
- **Nested Loops** - Loops within loops
- **Range & Enumerate** - Advanced iteration techniques

---

## 🔄 For Loops

### Basic For Loop

```python
# Loop through a list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# Output:
# apple
# banana
# cherry
```

### Loop with Range

```python
# Loop from 0 to 9
for i in range(10):
    print(i)

# Loop from 5 to 14
for i in range(5, 15):
    print(i)

# Loop from 0 to 20, step by 2
for i in range(0, 21, 2):
    print(i)  # Output: 0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20
```

### Loop Through Strings

```python
word = "Python"
for letter in word:
    print(letter)

# Output:
# P
# y
# t
# h
# o
# n
```

### Loop Through Dictionaries

```python
player = {"name": "Drago", "level": 5, "score": 1000}

# Loop through keys
for key in player:
    print(key)

# Loop through values
for value in player.values():
    print(value)

# Loop through key-value pairs
for key, value in player.items():
    print(f"{key}: {value}")
```

### Using Enumerate

```python
# Get both index and value
fruits = ["apple", "banana", "cherry"]
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# Output:
# 0: apple
# 1: banana
# 2: cherry

# Start index at 1
for index, fruit in enumerate(fruits, start=1):
    print(f"{index}: {fruit}")
```

---

## 🔁 While Loops

### Basic While Loop

```python
# Count from 1 to 5
counter = 1
while counter <= 5:
    print(counter)
    counter += 1

# Output: 1, 2, 3, 4, 5
```

### While with User Input

```python
# Keep asking until valid input
valid = False
while not valid:
    age = input("Enter your age: ")
    if age.isdigit():
        valid = True
        print(f"Your age is {age}")
    else:
        print("❌ Please enter a valid number!")
```

### Infinite Loop (Use with Care!)

```python
# This loop runs forever (or until you break out)
count = 0
while True:
    count += 1
    print(f"Count: {count}")
    if count >= 5:
        break  # Exit the loop
```

---

## 🛑 Break & Continue

### Break Statement

Break exits the loop immediately:

```python
# Stop when we find the number 3
for i in range(1, 10):
    if i == 3:
        break
    print(i)

# Output: 1, 2

# Search for item in list
items = [10, 20, 30, 40, 50]
search = 30
for item in items:
    if item == search:
        print(f"Found {search}!")
        break
else:
    print(f"{search} not found")
```

### Continue Statement

Continue skips to the next iteration:

```python
# Skip the number 3
for i in range(1, 6):
    if i == 3:
        continue
    print(i)

# Output: 1, 2, 4, 5

# Skip even numbers
for i in range(1, 11):
    if i % 2 == 0:
        continue
    print(i)  # Output: 1, 3, 5, 7, 9
```

---

## 🎯 Nested Loops

### Simple Nested Loop

```python
# Multiplication table
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i} × {j} = {i*j}")
    print("---")

# Output:
# 1 × 1 = 1
# 1 × 2 = 2
# 1 × 3 = 3
# ---
# 2 × 1 = 2
# 2 × 2 = 4
# 2 × 3 = 6
# ---
# (and so on...)
```

### Nested Loops with Lists

```python
# Check each player's score
players = ["Alice", "Bob", "Charlie"]
scores = [85, 90, 78]

for i, player in enumerate(players):
    print(f"{player}'s scores:")
    for score in scores:
        print(f"  {score}")
```

### Breaking Nested Loops

```python
# Search in 2D list
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

found = False
for row in matrix:
    for num in row:
        if num == 5:
            found = True
            break
    if found:
        break

print(f"Found 5 in matrix!")
```

---

## 🎮 Complete Example: Game Loop with Inventory

```python
# 🐉 DRAGOS PYTHON - Loops Demo

def display_inventory(items):
    """Display player's inventory"""
    print("\n📦 Your Inventory:")
    if not items:
        print("  (empty)")
    else:
        for i, item in enumerate(items, 1):
            print(f"  {i}. {item}")

def main():
    """Main game loop"""
    print("╔════════════════════════════════════╗")
    print("║  DRAGOS PYTHON - Inventory Game    ║")
    print("╚════════════════════════════════════╝")
    
    inventory = ["Sword", "Shield", "Potion"]
    
    while True:
        print("\n🎮 What would you like to do?")
        print("[1] View Inventory")
        print("[2] Add Item")
        print("[3] Remove Item")
        print("[4] Exit Game")
        
        choice = input("\nEnter choice (1-4): ")
        
        if choice == "1":
            display_inventory(inventory)
        
        elif choice == "2":
            item = input("Enter item to add: ")
            inventory.append(item)
            print(f"✅ Added {item} to inventory!")
        
        elif choice == "3":
            display_inventory(inventory)
            if inventory:
                try:
                    index = int(input("Enter item number to remove: ")) - 1
                    if 0 <= index < len(inventory):
                        removed = inventory.pop(index)
                        print(f"✅ Removed {removed} from inventory!")
                    else:
                        print("❌ Invalid item number!")
                except ValueError:
                    print("❌ Please enter a valid number!")
        
        elif choice == "4":
            print("\n👋 Thanks for playing! Goodbye!")
            break
        
        else:
            print("❌ Invalid choice! Please try again.")

if __name__ == "__main__":
    main()
```

---

## 🎮 Try It Yourself!

**Challenge 1: Counting Loop**
```python
# Print numbers 1 to 10, but skip 5
for i in range(1, 11):
    if i == 5:
        continue
    print(i)
```

**Challenge 2: Sum Calculator**
```python
# Sum numbers entered by user
total = 0
while True:
    num = input("Enter a number (or 'quit' to stop): ")
    if num.lower() == "quit":
        break
    try:
        total += float(num)
    except ValueError:
        print("❌ Please enter a valid number!")

print(f"Total: {total}")
```

**Challenge 3: Pattern Maker**
```python
# Create a triangle pattern
for i in range(1, 6):
    for j in range(i):
        print("*", end="")
    print()

# Output:
# *
# **
# ***
# ****
# *****
```

**Challenge 4: Find Maximum**
```python
# Find the maximum number in a list
numbers = [3, 7, 2, 9, 1, 5]
max_num = numbers[0]

for num in numbers:
    if num > max_num:
        max_num = num

print(f"Maximum: {max_num}")
```

---

## 📊 Loop Comparison

| Loop Type | Best For | Example |
|-----------|----------|---------|
| **For** | Known iterations | `for i in range(10)` |
| **While** | Unknown iterations | `while user_input != "quit"` |
| **Nested** | 2D structures | Matrix processing |

---

## 🔍 Key Takeaways

✅ For loops iterate over sequences (lists, strings, ranges)  
✅ While loops repeat until a condition is false  
✅ Break exits a loop immediately  
✅ Continue skips to the next iteration  
✅ Nested loops allow complex iterations  
✅ Enumerate gives you both index and value  

---

<div align="center">

**[← BACK](03-functions.md)** | **[↑ EXIT](../README.md)** | **[▶️ PLAY NOW](05-conditionals.md)**

</div>
