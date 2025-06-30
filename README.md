#program for hangman game

import random

word_list = ["apple", "banana", "orange", "grape", "peach"]

word = random.choice(word_list)
guessed_letters = []
correct_letters = []

max_incorrect = 6
incorrect_guesses = 0

print("Welcome to Hangman!")

while incorrect_guesses < max_incorrect:

    display_word = ""
    for letter in word:
        if letter in correct_letters:
            display_word += letter + " "
        else:
            display_word += "_ "
    print("\nWord:", display_word.strip())
    
  
    guess = input("Guess a letter: ").lower()
    
    if len(guess) != 1 or not guess.isalpha():
        print("Please enter a single letter.")
        continue
    
    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue
    
    guessed_letters.append(guess)
    
    if guess in word:
        print("Good guess!")
        correct_letters.append(guess)
    else:
        print("Wrong guess!")
        incorrect_guesses += 1
        print(f"Incorrect guesses left: {max_incorrect - incorrect_guesses}")
    

    if all(letter in correct_letters for letter in word):
        print(f"\nCongratulations! You guessed the word: {word}")
        break
else:
    print(f"\nGame Over! The word was: {word}")
