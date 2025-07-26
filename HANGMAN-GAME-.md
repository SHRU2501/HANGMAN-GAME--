# HANGMAN-GAME- A simple text-based Hangman game in Python
import random
logo = r"""
 _                                             
| |                                            
| |__   __ _ _ __   __ _ _ __ ___   __ _ _ __  
| '_ \ / _` | '_ \ / _` | '_ ` _ \ / _` | '_ \ 
| | | | (_| | | | | (_| | | | | | | (_| | | | |
|_| |_|\__,_|_| |_|\__, |_| |_| |_|\__,_|_| |_|
                    __/ |                      
                   |___/                       
"""
print(logo)

#Hangman ASCII Art Stages
HANGMANPICS = [r"""
  +---+
  |   |
      |
      |
      |
      |
=========""", r"""
  +---+
  |   |
  O   |
      |
      |
      |
=========""", r"""
  +---+
  |   |
  O   |
  |   |
      |
      |
=========""", r"""
  +---+
  |   |
  O   |
 /|   |
      |
      |
=========""", r"""
  +---+
  |   |
  O   |
 /|\  |
      |
      |
=========""", r"""
  +---+
  |   |
  O   |
 /|\  |
 /    |
      |
=========""", r"""
  +---+
  |   |
  O   |
 /|\  |
 / \  |
      |
========="""
]

# Word pool
words = ["apple","cheery","car","animal","laptop"]
word = random.choice(words)
guessed = []
wrong_guesses = 0
max_wrong = len(HANGMANPICS) - 1
print(" Welcome to Hangman!")
print("_ " * len(word))

while wrong_guesses < max_wrong:
    print(HANGMANPICS[wrong_guesses])
    
    display = ""
    failed = 0
    for char in word:
        if char in guessed:
            display += char + " "
        else:
            display += "_ "
            failed += 1
    print("Word:", display)

    if failed == 0:
        print(" You won! The word was:", word)
        break

    guess = input(" Guess a letter: ").lower()

    if not guess.isalpha() or len(guess) != 1:
        print(" Please enter a single alphabet letter.")
        continue
    if guess in guessed:
        print("You already guessed that letter.")
        continue

    guessed.append(guess)

    if guess not in word:
        wrong_guesses += 1
        print("Wrong guess! Turns left:", max_wrong - wrong_guesses)

if wrong_guesses == max_wrong:
    print(HANGMANPICS[wrong_guesses])
    print(" Game over! The word was:", word)
print("Thanks for playing Hangman!")

# How to run
# 1. Save this code in a file named `hangman.py`.
# 2. Open a terminal and navigate to the directory where the file is saved.
# 3. Run the command `python hangman.py` to start the game. 
# 4. Follow the prompts to guess letters and solve the word.
# 5. Enjoy the game and try to avoid the hangman!
