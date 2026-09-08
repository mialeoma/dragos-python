# 7️⃣ GAME DEVELOPMENT
## Create Your First Game with Python

---

## 📚 What You'll Learn

- **Game Loop** - Core game mechanics
- **Pygame Basics** - Graphics and events
- **Player Movement** - Keyboard controls
- **Collision Detection** - Object interactions
- **Score System** - Track game progress

---

## 🎮 Introduction to Game Development

### What is a Game Loop?

A game loop is the heart of every game. It runs continuously and does three things:

1. **Handle Input** - Listen for keyboard/mouse events
2. **Update** - Update game state (positions, scores, etc.)
3. **Render** - Draw everything on screen

```python
# Basic game loop structure
while game_running:
    # 1. Handle input
    for event in get_events():
        if event.type == QUIT:
            game_running = False
    
    # 2. Update game state
    update_game()
    
    # 3. Render (draw)
    draw_screen()
```

---

## 🎯 Game 1: Simple Number Adventure

**Difficulty:** 🟢 Beginner

A text-based game where players navigate through a story.

```python
# 🐉 DRAGOS PYTHON - Number Adventure

def start_game():
    """Main game loop for Number Adventure"""
    print("╔════════════════════════════════════╗")
    print("║   DRAGOS PYTHON - Number Adventure ║")
    print("╚════════════════════════════════════╝\n")
    
    print("You are a brave adventurer!")
    print("You encounter three paths:\n")
    
    while True:
        print("[1] Forest Path 🌲")
        print("[2] Mountain Path ⛰️")
        print("[3] Ocean Path 🌊")
        print("[4] Exit Game")
        
        choice = input("\nChoose your path (1-4): ")
        
        if choice == "1":
            forest_adventure()
        elif choice == "2":
            mountain_adventure()
        elif choice == "3":
            ocean_adventure()
        elif choice == "4":
            print("\n👋 Thanks for playing! Goodbye!")
            break
        else:
            print("❌ Invalid choice!")

def forest_adventure():
    """Forest path scenario"""
    print("\n🌲 You enter the forest...")
    print("You find a treasure chest!")
    
    choice = input("Open it? (yes/no): ").lower()
    
    if choice == "yes":
        print("✨ You found 100 gold coins! 💰")
    else:
        print("You walk away from the chest... (no reward)")

def mountain_adventure():
    """Mountain path scenario"""
    print("\n⛰️ You climb the mountain...")
    print("You reach the peak!")
    
    import random
    treasure = random.randint(50, 200)
    print(f"✨ You found {treasure} gold coins! 💰")

def ocean_adventure():
    """Ocean path scenario"""
    print("\n🌊 You sail the ocean...")
    print("You encounter a pirate ship!")
    
    import random
    if random.random() > 0.5:
        print("⚔️ You defeat the pirates!")
        print("✨ You found 150 gold coins! 💰")
    else:
        print("😢 You lost the battle...")
        print("You escape with 10 gold coins! 💰")

if __name__ == "__main__":
    start_game()
```

---

## 🎯 Game 2: Hangman

**Difficulty:** 🟠 Intermediate

A classic word guessing game.

```python
# 🐉 DRAGOS PYTHON - Hangman Game

import random

def hangman():
    """Play Hangman game"""
    # Word list
    words = ["python", "dragon", "adventure", "wizard", "treasure", "magic"]
    secret_word = random.choice(words)
    guessed_letters = []
    correct_guesses = []
    wrong_guesses = 0
    max_wrong = 6
    
    print("╔════════════════════════════════════╗")
    print("║       DRAGOS PYTHON - HANGMAN      ║")
    print("╚════════════════════════════════════╝\n")
    
    while wrong_guesses < max_wrong:
        # Display hangman
        display_hangman(wrong_guesses)
        
        # Display word progress
        display_word = ""
        for letter in secret_word:
            if letter in correct_guesses:
                display_word += letter + " "
            else:
                display_word += "_ "
        
        print(f"\nWord: {display_word}")
        print(f"Wrong guesses: {wrong_guesses}/{max_wrong}")
        print(f"Guessed letters: {', '.join(guessed_letters)}")
        
        # Check if won
        if all(letter in correct_guesses for letter in secret_word):
            print(f"\n🎉 You won! The word was: {secret_word}")
            return
        
        # Get guess
        guess = input("\nGuess a letter: ").lower()
        
        if len(guess) != 1 or not guess.isalpha():
            print("❌ Enter a single letter!")
            continue
        
        if guess in guessed_letters:
            print("⚠️ Already guessed!")
            continue
        
        guessed_letters.append(guess)
        
        # Check guess
        if guess in secret_word:
            correct_guesses.append(guess)
            print(f"✅ Correct! '{guess}' is in the word!")
        else:
            wrong_guesses += 1
            print(f"❌ Wrong! '{guess}' is not in the word!")
    
    print(f"\n💀 Game Over! The word was: {secret_word}")

def display_hangman(tries):
    """Display hangman stages"""
    stages = [
        "  +---+\n  |   |\n      |\n      |\n      |\n      |\n=========",
        "  +---+\n  |   |\n  O   |\n      |\n      |\n      |\n=========",
        "  +---+\n  |   |\n  O   |\n  |   |\n      |\n      |\n=========",
        "  +---+\n  |   |\n  O   |\n /|   |\n      |\n      |\n=========",
        "  +---+\n  |   |\n  O   |\n /|\\  |\n      |\n      |\n=========",
        "  +---+\n  |   |\n  O   |\n /|\\  |\n /    |\n      |\n=========",
        "  +---+\n  |   |\n  O   |\n /|\\  |\n / \\  |\n      |\n========="
    ]
    print(stages[tries])

if __name__ == "__main__":
    hangman()
```

---

## 🎯 Game 3: Rock, Paper, Scissors

**Difficulty:** 🟢 Beginner

Classic game against the computer.

```python
# 🐉 DRAGOS PYTHON - Rock Paper Scissors

import random

def rock_paper_scissors():
    """Play Rock Paper Scissors"""
    print("╔════════════════════════════════════╗")
    print("║  DRAGOS PYTHON - Rock Paper Scissors║")
    print("╚════════════════════════════════════╝\n")
    
    choices = ["rock", "paper", "scissors"]
    player_score = 0
    computer_score = 0
    
    while True:
        print(f"\nScore - You: {player_score} | Computer: {computer_score}")
        print("[1] Rock 🪨")
        print("[2] Paper 📄")
        print("[3] Scissors ✂️")
        print("[4] Quit")
        
        choice = input("\nYour choice (1-4): ")
        
        if choice == "4":
            print(f"\n🏆 Final Score - You: {player_score} | Computer: {computer_score}")
            print("👋 Thanks for playing!")
            break
        
        if choice in ["1", "2", "3"]:
            player_choice = choices[int(choice) - 1]
            computer_choice = random.choice(choices)
            
            print(f"\nYou chose: {player_choice} 🎮")
            print(f"Computer chose: {computer_choice} 🤖")
            
            # Determine winner
            if player_choice == computer_choice:
                print("It's a tie! 🤝")
            elif wins(player_choice, computer_choice):
                print("✅ You win! 🎉")
                player_score += 1
            else:
                print("❌ Computer wins! 💻")
                computer_score += 1
        else:
            print("❌ Invalid choice!")

def wins(player, computer):
    """Check if player wins"""
    if player == "rock" and computer == "scissors":
        return True
    if player == "paper" and computer == "rock":
        return True
    if player == "scissors" and computer == "paper":
        return True
    return False

if __name__ == "__main__":
    rock_paper_scissors()
```

---

## 🎯 Game 4: Battle Arena (Advanced)

**Difficulty:** 🔴 Advanced

A turn-based combat game with characters and abilities.

```python
# 🐉 DRAGOS PYTHON - Battle Arena

import random

class Character:
    def __init__(self, name, health, attack_power):
        self.name = name
        self.health = health
        self.max_health = health
        self.attack_power = attack_power
    
    def attack(self):
        """Return random damage"""
        return random.randint(self.attack_power // 2, self.attack_power)
    
    def take_damage(self, damage):
        """Reduce health"""
        self.health -= damage
        if self.health < 0:
            self.health = 0
    
    def heal(self, amount):
        """Restore health"""
        self.health += amount
        if self.health > self.max_health:
            self.health = self.max_health
    
    def is_alive(self):
        """Check if character is alive"""
        return self.health > 0
    
    def display_status(self):
        """Show character status"""
        health_bar = "█" * (self.health // 10) + "░" * ((self.max_health - self.health) // 10)
        print(f"{self.name}: {health_bar} ({self.health}/{self.max_health})")

def battle_arena():
    """Main battle game"""
    print("╔════════════════════════════════════╗")
    print("║    DRAGOS PYTHON - Battle Arena    ║")
    print("╚════════════════════════════════════╝\n")
    
    # Create characters
    player = Character("Hero", 100, 20)
    enemy = Character("Dragon", 80, 15)
    
    print(f"🎮 You face a {enemy.name}!\n")
    
    turn = 0
    while player.is_alive() and enemy.is_alive():
        turn += 1
        print(f"\n--- Turn {turn} ---")
        
        # Display status
        player.display_status()
        enemy.display_status()
        
        # Player action
        print("\n[1] Attack ⚔️")
        print("[2] Heal 🏥")
        print("[3] Defend 🛡️")
        
        choice = input("\nYour action (1-3): ")
        
        if choice == "1":
            damage = player.attack()
            enemy.take_damage(damage)
            print(f"⚔️ You attack for {damage} damage!")
        
        elif choice == "2":
            player.heal(30)
            print(f"🏥 You heal for 30 health!")
        
        elif choice == "3":
            print("🛡️ You defend! Damage reduced!")
            damage = enemy.attack() // 2
            player.take_damage(damage)
            print(f"The dragon attacks for {damage} damage!")
            continue
        
        else:
            print("❌ Invalid action!")
            continue
        
        # Enemy turn
        enemy_action = random.choice(["attack", "heal"])
        
        if enemy_action == "attack":
            damage = enemy.attack()
            player.take_damage(damage)
            print(f"🐉 Dragon attacks for {damage} damage!")
        else:
            enemy.heal(20)
            print("🐉 Dragon heals for 20 health!")
    
    # Determine winner
    print("\n" + "="*35)
    if player.is_alive():
        print("🏆 Victory! You defeated the dragon!")
    else:
        print("💀 Defeat! The dragon was too strong!")

if __name__ == "__main__":
    battle_arena()
```

---

## 🎮 Game Development Tips

### Good Game Design

✅ Clear objectives and rules  
✅ Engaging mechanics and feedback  
✅ Progressive difficulty  
✅ Balanced challenges  
✅ Fun and entertaining  

### Code Organization

✅ Use functions for different game states  
✅ Create classes for game objects  
✅ Separate logic from display  
✅ Keep game loop clean and simple  

### Testing & Debugging

✅ Test all user inputs  
✅ Handle edge cases  
✅ Test win/lose conditions  
✅ Check for infinite loops  

---

## 🚀 Next Steps

**You've completed all modules!** What to do next:

1. **Combine Games** - Create a game launcher that runs all games
2. **Add Features** - Add sound, difficulty levels, leaderboards
3. **Use Pygame** - Learn graphics library for more advanced games
4. **Join Communities** - Share your games with other Python developers
5. **Keep Learning** - Explore OOP, data structures, and algorithms

---

## 📚 Recommended Resources

- **Pygame Documentation** - https://www.pygame.org/docs/
- **Real Python Guides** - https://realpython.com/
- **Python.org Tutorial** - https://docs.python.org/3/tutorial/
- **Game Dev Communities** - itch.io, Game Jams

---

## 🏆 Congratulations!

You've learned:
- ✅ Variables and data types
- ✅ Functions and methods
- ✅ Loops and iterations
- ✅ Conditionals and logic
- ✅ Error handling
- ✅ File operations
- ✅ Game development basics

**You are now ready to build amazing things with Python!** 🚀

---

<div align="center">

**[← BACK](06-challenges.md)** | **[↑ EXIT](../README.md)** | **[🎉 COMPLETE](#game-development)**

</div>
