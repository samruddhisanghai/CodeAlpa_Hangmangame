# CodeAlpa_Hangmangame
#a word guess game 
import random

# Predefined list of 5 words
words = ["python", "coding", "hangman", "logic", "simple"]
secret_word = random.choice(words)
guessed_letters = []
attempts = 6

print("Welcome to Hangman!")

while attempts > 0:
    # Display the current state of the word
    display_word = ""
    for letter in secret_word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "
    
    print(f"\nWord: {display_word}")
    print(f"Attempts left: {attempts}")
    
    # Check if the player has won
    if "_" not in display_word:
        print("Congratulations! You won!")
        break

    guess = input("Guess a letter: ").lower()

    # Input validation
    if len(guess) != 1 or not guess.isalpha():
        print("Please enter a single valid letter.")
        continue
    
    if guess in guessed_letters:
        print(f"You already guessed '{guess}'.")
        continue

    guessed_letters.append(guess)

    # Check if the guess is correct
    if guess in secret_word:
        print("Good guess!")
    else:
        attempts -= 1
        print(f"Wrong! '{guess}' is not in the word.")

if attempts == 0:
    print(f"\nGame Over! The word was: {secret_word}")
