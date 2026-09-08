# 5️⃣ IF-ELSE STATEMENTS
## Conditionals, Logic, Boolean Operations & Decision Making

---

## 📚 What You'll Learn

- **If Statements** - Execute code based on conditions
- **Else & Elif** - Multiple branches
- **Boolean Operations** - AND, OR, NOT
- **Comparison Operators** - Compare values
- **Nested Conditionals** - Complex decision making

---

## 🎯 Comparison Operators

### Basic Comparisons

```python
# Equal to
5 == 5          # True
5 == 3          # False

# Not equal to
5 != 3          # True
5 != 5          # False

# Greater than
5 > 3           # True
3 > 5           # False

# Less than
3 < 5           # True
5 < 3           # False

# Greater than or equal to
5 >= 5          # True
5 >= 3          # True

# Less than or equal to
3 <= 5          # True
5 <= 5          # True
```

---

## ✅ If Statements

### Basic If

```python
age = 18

if age >= 18:
    print("✅ You are an adult!")

# Output: ✅ You are an adult!
```

### If-Else

```python
age = 15

if age >= 18:
    print("✅ You are an adult!")
else:
    print("⚠️ You are still a minor!")

# Output: ⚠️ You are still a minor!
```

### If-Elif-Else

```python
score = 85

if score >= 90:
    print("🥇 Grade: A")
elif score >= 80:
    print("🥈 Grade: B")
elif score >= 70:
    print("🥉 Grade: C")
elif score >= 60:
    print("📊 Grade: D")
else:
    print("❌ Grade: F")

# Output: 🥈 Grade: B
```

---

## 🔗 Boolean Operations

### AND Operator

All conditions must be True:

```python
age = 25
has_license = True

if age >= 18 and has_license:
    print("✅ You can drive!")
else:
    print("❌ You cannot drive!")

# Output: ✅ You can drive!
```

### OR Operator

At least one condition must be True:

```python
day = "Saturday"

if day == "Saturday" or day == "Sunday":
    print("🎉 It's the weekend!")
else:
    print("📚 It's a weekday!")

# Output: 🎉 It's the weekend!
```

### NOT Operator

Inverts the boolean value:

```python
is_raining = False

if not is_raining:
    print("☀️ Let's go outside!")
else:
    print("🌧️ Stay inside!")

# Output: ☀️ Let's go outside!
```

### Combining Operators

```python
age = 25
has_license = True
is_sober = True

if age >= 18 and has_license and is_sober:
    print("✅ Safe to drive!")
else:
    print("❌ Not safe to drive!")

# Using parentheses for clarity
if (age >= 18 and has_license) or (age >= 16 and has_license and has_guardian):
    print("✅ Can drive!")
```

---

## 📊 Membership & Identity Operators

### In & Not In

```python
fruits = ["apple", "banana", "cherry"]

if "apple" in fruits:
    print("✅ Apple is in the list!")

if "orange" not in fruits:
    print("✅ Orange is not in the list!")
```

### Is & Is Not

```python
# Check if variables refer to same object
a = [1, 2, 3]
b = [1, 2, 3]
c = a

print(a == b)       # True (same content)
print(a is b)       # False (different objects)
print(a is c)       # True (same object)

x = None
if x is None:
    print("✅ x is None")
```

---

## 🎯 Nested Conditionals

### Multiple Levels

```python
score = 85
level = "Advanced"

if score >= 70:
    print("✅ You passed!")
    
    if score >= 90:
        print("🏆 Outstanding!")
    elif score >= 80:
        print("🌟 Great job!")
    else:
        print("👍 Good effort!")
else:
    print("❌ You failed!")
```

---

## 🎮 Complete Example: Adventure Game

```python
# 🐉 DRAGOS PYTHON - Conditionals Demo

def play_game():
    """Play an adventure game"""
    print("╔════════════════════════════════════╗")
    print("║    DRAGOS PYTHON - Adventure       ║")
    print("╚════════════════════════════════════╝\n")
    
    print("You encounter a dragon! 🐉")
    print("What do you do?")
    print("[1] Fight the dragon")
    print("[2] Run away")
    print("[3] Try to negotiate")
    
    choice = input("\nYour choice (1-3): ")
    
    if choice == "1":
        print("\n⚔️ You draw your sword and charge!")
        strength = int(input("What's your strength level (1-100)? "))
        
        if strength >= 80:
            print("✅ You defeated the dragon!")
            print("🏆 You are a true hero!")
        elif strength >= 50:
            print("⚔️ Epic battle! You barely win!")
            print("🎉 Victory!")
        else:
            print("😢 The dragon is too strong!")
            print("💀 You lost the battle!")
    
    elif choice == "2":
        print("\n🏃 You run away from the dragon!")
        agility = int(input("What's your agility level (1-100)? "))
        
        if agility >= 70:
            print("✅ You escape safely!")
        else:
            print("😢 The dragon catches you!")
            print("💀 You didn't make it!")
    
    elif choice == "3":
        print("\n💬 You try to talk to the dragon...")
        charisma = int(input("What's your charisma level (1-100)? "))
        has_treasure = input("Do you have treasure to offer? (yes/no): ")
        
        if (charisma >= 60 and has_treasure.lower() == "yes") or charisma >= 90:
            print("✨ The dragon is impressed!")
            print("🤝 You become friends with the dragon!")
            print("🏆 You gained a powerful ally!")
        else:
            print("😢 The dragon is not interested!")
            print("💀 The dragon attacks!")
    
    else:
        print("\n❌ Invalid choice! The dragon attacks while you hesitate!")
        print("💀 Game Over!")

if __name__ == "__main__":
    play_game()
```

---

## 🎮 Try It Yourself!

**Challenge 1: Age Validator**
```python
age = int(input("Enter your age: "))

if age < 0:
    print("❌ Age cannot be negative!")
elif age < 13:
    print("👶 You are a child!")
elif age < 18:
    print("👨 You are a teenager!")
elif age < 65:
    print("👴 You are an adult!")
else:
    print("🧓 You are a senior!")
```

**Challenge 2: Login System**
```python
username = input("Enter username: ")
password = input("Enter password: ")

if username == "admin" and password == "12345":
    print("✅ Login successful!")
elif username == "admin":
    print("❌ Wrong password!")
else:
    print("❌ Username not found!")
```

**Challenge 3: Grade Calculator**
```python
math = int(input("Math score: "))
english = int(input("English score: "))
science = int(input("Science score: "))

average = (math + english + science) / 3

if average >= 90:
    print(f"🥇 Grade: A (Average: {average:.1f})")
elif average >= 80:
    print(f"🥈 Grade: B (Average: {average:.1f})")
elif average >= 70:
    print(f"🥉 Grade: C (Average: {average:.1f})")
else:
    print(f"❌ Grade: F (Average: {average:.1f})")
```

**Challenge 4: Password Strength Checker**
```python
password = input("Enter a password: ")
length = len(password)
has_upper = any(c.isupper() for c in password)
has_lower = any(c.islower() for c in password)
has_digit = any(c.isdigit() for c in password)

if length >= 8 and has_upper and has_lower and has_digit:
    print("✅ Strong password!")
elif length >= 6 and (has_upper or has_lower) and has_digit:
    print("⚠️ Medium password!")
else:
    print("❌ Weak password!")
```

---

## 🔍 Conditional Truth Table

| Condition | Result |
|-----------|--------|
| `True and True` | True |
| `True and False` | False |
| `False and False` | False |
| `True or True` | True |
| `True or False` | True |
| `False or False` | False |
| `not True` | False |
| `not False` | True |

---

## 🔍 Key Takeaways

✅ Use comparison operators to compare values  
✅ If statements execute code conditionally  
✅ Elif allows multiple branches  
✅ AND, OR, NOT combine conditions  
✅ In/Not In check membership  
✅ Nested conditionals handle complex logic  

---

<div align="center">

**[← BACK](04-loops.md)** | **[↑ EXIT](../README.md)** | **[▶️ PLAY NOW](06-challenges.md)**

</div>
