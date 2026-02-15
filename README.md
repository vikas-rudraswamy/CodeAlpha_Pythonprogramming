import random

def play_hangman():
    words = ["python", "computer", "science", "program", "hangman"]
    secret_word = random.choice(words)
    
    guessed_letters = []
    wrong_guesses = 0
    max_attempts = 6

    print(" Welcome to Hangman Game!")
    print("You have 6 incorrect attempts. Good luck!\n")

    while wrong_guesses < max_attempts:
        display_word = ""
        for letter in secret_word:
            if letter in guessed_letters:
                display_word += letter + " "
            else:
                display_word += "_ "
        
        print("Word:", display_word.strip())
        print("Wrong attempts left:", max_attempts - wrong_guesses)
        if all(letter in guessed_letters for letter in secret_word):
            print("\nCongratulations! You guessed the word correctly:", secret_word)
            return
        guess = input("Enter a letter: ").lower()
        if len(guess) != 1 or not guess.isalpha():
            print(" Please enter a single valid alphabet letter.\n")
            continue

        if guess in guessed_letters:
            print(" You already guessed that letter.\n")
            continue
        if guess in secret_word:
            print("Correct guess!\n")
            guessed_letters.append(guess)
        else:
            print("sorry it is a wrong guess!\n")
            guessed_letters.append(guess)
            wrong_guesses += 1

    # If loop ends, player lost
    print("Game Over! The correct word was:", secret_word)

if __name__ == "__main__":
    play_hangman()
