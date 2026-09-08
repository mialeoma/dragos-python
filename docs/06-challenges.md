# 6️⃣ CHALLENGES & QUESTS
## Practical Exercises to Master Python Fundamentals

---

## 📚 Challenge Overview

Complete these challenges to test your Python skills! Each challenge builds on what you've learned in the previous modules.

---

## 🎯 Challenge 1: Number Guessing Game

**Difficulty:** 🟢 Beginner

**Objective:** Create a game where the computer picks a random number and the player tries to guess it.

**Requirements:**
- Import the `random` module
- Generate a random number between 1 and 100
- Give hints (too high/too low)
- Count attempts
- Congratulate player on success

**Starter Code:**
```python
import random

def guessing_game():
    """Number guessing game"""
    secret_number = random.randint(1, 100)
    attempts = 0
    guessed = False
    
    print("🎮 Welcome to the Number Guessing Game!")
    print("I'm thinking of a number between 1 and 100...")
    
    while not guessed:
        try:
            guess = int(input("Enter your guess: "))
            attempts += 1
            
            if guess < secret_number:
                print("📈 Too low! Try again.")
            elif guess > secret_number:
                print("📉 Too high! Try again.")
            else:
                print(f"🎉 Correct! You guessed it in {attempts} attempts!")
                guessed = True
        
        except ValueError:
            print("❌ Please enter a valid number!")

if __name__ == "__main__":
    guessing_game()
```

---

## 🎯 Challenge 2: To-Do List Manager

**Difficulty:** 🟠 Intermediate

**Objective:** Create a program to manage a to-do list with add, remove, and display functions.

**Requirements:**
- Add tasks to the list
- Remove tasks from the list
- Display all tasks
- Mark tasks as complete
- Save to file

**Starter Code:**
```python
def display_menu():
    """Display the to-do list menu"""
    print("\n📋 To-Do List Manager")
    print("[1] View Tasks")
    print("[2] Add Task")
    print("[3] Remove Task")
    print("[4] Mark as Complete")
    print("[5] Exit")

def main():
    """Main to-do list program"""
    tasks = []
    
    while True:
        display_menu()
        choice = input("Enter choice (1-5): ")
        
        if choice == "1":
            if tasks:
                for i, task in enumerate(tasks, 1):
                    print(f"{i}. {task}")
            else:
                print("No tasks yet!")
        
        elif choice == "2":
            task = input("Enter new task: ")
            tasks.append(task)
            print("✅ Task added!")
        
        elif choice == "3":
            if tasks:
                for i, task in enumerate(tasks, 1):
                    print(f"{i}. {task}")
                try:
                    index = int(input("Task number to remove: ")) - 1
                    if 0 <= index < len(tasks):
                        removed = tasks.pop(index)
                        print(f"✅ Removed: {removed}")
                except ValueError:
                    print("❌ Invalid number!")
        
        elif choice == "5":
            print("👋 Goodbye!")
            break
        
        else:
            print("❌ Invalid choice!")

if __name__ == "__main__":
    main()
```

---

## 🎯 Challenge 3: Calculator with History

**Difficulty:** 🟠 Intermediate

**Objective:** Build a calculator that performs operations and keeps a history.

**Requirements:**
- Perform basic arithmetic (+, -, *, /)
- Keep calculation history
- Display history
- Clear history option
- Error handling for division by zero

**Starter Code:**
```python
def calculator():
    """Calculator with history"""
    history = []
    
    print("╔════════════════════════════════════╗")
    print("║      Calculator with History       ║")
    print("╚════════════════════════════════════╝")
    
    while True:
        print("\n[1] Calculate")
        print("[2] View History")
        print("[3] Clear History")
        print("[4] Exit")
        
        choice = input("Choice: ")
        
        if choice == "1":
            try:
                num1 = float(input("First number: "))
                operation = input("Operation (+, -, *, /): ")
                num2 = float(input("Second number: "))
                
                if operation == "+":
                    result = num1 + num2
                elif operation == "-":
                    result = num1 - num2
                elif operation == "*":
                    result = num1 * num2
                elif operation == "/":
                    if num2 == 0:
                        print("❌ Cannot divide by zero!")
                        continue
                    result = num1 / num2
                else:
                    print("❌ Invalid operation!")
                    continue
                
                calculation = f"{num1} {operation} {num2} = {result}"
                history.append(calculation)
                print(f"Result: {result}")
            
            except ValueError:
                print("❌ Please enter valid numbers!")
        
        elif choice == "2":
            if history:
                print("\n📝 History:")
                for i, calc in enumerate(history, 1):
                    print(f"{i}. {calc}")
            else:
                print("No history yet!")
        
        elif choice == "3":
            history.clear()
            print("✅ History cleared!")
        
        elif choice == "4":
            print("👋 Goodbye!")
            break

if __name__ == "__main__":
    calculator()
```

---

## 🎯 Challenge 4: Password Strength Checker

**Difficulty:** 🟠 Intermediate

**Objective:** Analyze a password and provide feedback on its strength.

**Requirements:**
- Check minimum length (8 characters)
- Check for uppercase letters
- Check for lowercase letters
- Check for numbers
- Check for special characters
- Provide strength rating (Weak/Medium/Strong)

**Starter Code:**
```python
def check_password_strength(password):
    """Check password strength"""
    strength = 0
    feedback = []
    
    # Length check
    if len(password) >= 8:
        strength += 1
    else:
        feedback.append("❌ Password too short (min 8 characters)")
    
    # Uppercase check
    if any(c.isupper() for c in password):
        strength += 1
    else:
        feedback.append("❌ Add uppercase letters")
    
    # Lowercase check
    if any(c.islower() for c in password):
        strength += 1
    else:
        feedback.append("❌ Add lowercase letters")
    
    # Number check
    if any(c.isdigit() for c in password):
        strength += 1
    else:
        feedback.append("❌ Add numbers")
    
    # Special character check
    special_chars = "!@#$%^&*()_+-=[]{}|;:,.<>?"
    if any(c in special_chars for c in password):
        strength += 1
    else:
        feedback.append("❌ Add special characters")
    
    # Rate strength
    if strength <= 2:
        rating = "🔴 Weak"
    elif strength <= 3:
        rating = "🟡 Medium"
    else:
        rating = "🟢 Strong"
    
    return rating, feedback

def main():
    print("🔐 Password Strength Checker")
    password = input("Enter password: ")
    rating, feedback = check_password_strength(password)
    
    print(f"\nStrength: {rating}")
    if feedback:
        print("\nSuggestions:")
        for item in feedback:
            print(f"  {item}")
    else:
        print("\n✅ Excellent password!")

if __name__ == "__main__":
    main()
```

---

## 🎯 Challenge 5: File Organizer

**Difficulty:** 🟠 Intermediate

**Objective:** Create a program that organizes files by extension into folders.

**Requirements:**
- Scan a directory
- Group files by extension
- Display file organization
- Create summary report
- Handle errors gracefully

**Starter Code:**
```python
import os
from collections import defaultdict

def organize_files(directory):
    """Organize files by extension"""
    file_groups = defaultdict(list)
    
    try:
        # Get all files in directory
        files = os.listdir(directory)
        
        for file in files:
            if os.path.isfile(os.path.join(directory, file)):
                # Get file extension
                _, ext = os.path.splitext(file)
                if ext:
                    file_groups[ext].append(file)
                else:
                    file_groups["no_extension"].append(file)
        
        # Display results
        print(f"\n📁 Files in {directory}:")
        for ext, files_list in sorted(file_groups.items()):
            print(f"\n{ext} ({len(files_list)} files):")
            for file in files_list:
                print(f"  - {file}")
        
        # Summary
        total_files = sum(len(files_list) for files_list in file_groups.values())
        print(f"\n📊 Total: {total_files} files")
    
    except FileNotFoundError:
        print(f"❌ Directory not found: {directory}")
    except Exception as e:
        print(f"❌ Error: {e}")

if __name__ == "__main__":
    directory = input("Enter directory path: ")
    organize_files(directory)
```

---

## 🎯 Challenge 6: Dice Rolling Simulator

**Difficulty:** 🟢 Beginner

**Objective:** Simulate rolling dice with various options.

**Requirements:**
- Roll single or multiple dice
- Support different dice types (d6, d12, d20)
- Display results
- Calculate total
- Show statistics

**Starter Code:**
```python
import random

def roll_dice(num_dice=1, sides=6):
    """Roll dice and return results"""
    rolls = [random.randint(1, sides) for _ in range(num_dice)]
    return rolls

def main():
    print("🎲 Dice Rolling Simulator")
    
    while True:
        print("\n[1] Roll Dice")
        print("[2] Exit")
        
        choice = input("Choice: ")
        
        if choice == "1":
            try:
                num_dice = int(input("How many dice? "))
                sides = int(input("How many sides? (6, 12, 20): "))
                
                if num_dice <= 0 or sides <= 0:
                    print("❌ Please enter positive numbers!")
                    continue
                
                rolls = roll_dice(num_dice, sides)
                total = sum(rolls)
                
                print(f"\n🎲 Rolls: {rolls}")
                print(f"📊 Total: {total}")
                print(f"📈 Average: {total/num_dice:.2f}")
            
            except ValueError:
                print("❌ Please enter valid numbers!")
        
        elif choice == "2":
            print("👋 Goodbye!")
            break

if __name__ == "__main__":
    main()
```

---

## 🏆 Challenge Completion Checklist

- [ ] Challenge 1: Number Guessing Game ✅
- [ ] Challenge 2: To-Do List Manager ✅
- [ ] Challenge 3: Calculator with History ✅
- [ ] Challenge 4: Password Strength Checker ✅
- [ ] Challenge 5: File Organizer ✅
- [ ] Challenge 6: Dice Rolling Simulator ✅

**Congratulations! You're ready for Game Development!** 🎉

---

## 💡 Tips for Success

✅ Start simple and add features gradually  
✅ Test your code frequently  
✅ Handle errors gracefully  
✅ Write clear comments  
✅ Use functions to organize code  
✅ Don't be afraid to experiment!  

---

## 🔍 Key Concepts Used

- Variables and data types
- Input/output
- Functions
- Loops
- Conditionals
- Error handling
- File operations
- Modules and imports

---

<div align="center">

**[← BACK](05-conditionals.md)** | **[↑ EXIT](../README.md)** | **[▶️ PLAY NOW](07-game-dev.md)**

</div>
