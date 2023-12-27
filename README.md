# Hangman-Game2
 Implement a simple text-based Hangman game in Python.
import random

def choose_word():
    words = ['python', 'hangman', 'programming', 'coding', 'challenge']
    return random.choice(words)

def display_word(word, guessed_letters):
    display = ''
    for letter in word:
        if letter in guessed_letters:
            display += letter
        else:
            display += '_'
    return display

def hangman():
    secret_word = choose_word()
    guessed_letters = []
    attempts = 6

    print("Welcome to Hangman!")
    while attempts > 0:
        guess = input(f"Word: {display_word(secret_word, guessed_letters)}\nGuess a letter: ").lower()

        if guess in guessed_letters:
            print("You already guessed that letter. Try again.")
            continue

        guessed_letters.append(guess)

        if guess not in secret_word:
            attempts -= 1
            print(f"Incorrect! {attempts} attempts remaining.")
        else:
            print("Correct!")

        if all(letter in guessed_letters for letter in secret_word):
            print(f"Congratulations! You guessed the word: {secret_word}")
            break

    if attempts == 0:
        print(f"Out of attempts! The word was: {secret_word}")

hangman()
