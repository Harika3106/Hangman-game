import random

# List of words to choose from
words = ['python', 'hangman', 'programming', 'developer', 'function', 'variable', 'loop', 'keyboard', 'syntax']

def choose_word():
    return random.choice(words).lower()

def display_word(word, guessed_letters):
    return ''.join([letter if letter in guessed_letters else '_' for letter in word])

def hangman():
    print("🎮 Welcome to Hangman Game! 🎮")
    word = choose_word()
    guessed_letters = set()
    attempts = 6

    print("\nLet's start! Guess the word:")
    while attempts > 0:
        print(f"\nWord: {display_word(word, guessed_letters)}")
        guess = input("Guess a letter: ").lower()

        if len(guess) != 1 or not guess.isalpha():
            print("❌ Please enter a valid single letter.")
            continue

        if guess in guessed_letters:
            print("⚠️ You've already guessed that letter.")
            continue

        guessed_letters.add(guess)

        if guess in word:
            print(f"✅ Good guess! '{guess}' is in the word.")
            if set(word) <= guessed_letters:
                print(f"🎉 Congratulations! You guessed the word '{word}' correctly!")
                break
        else:
            attempts -= 1
            print(f"❌ Wrong guess. Attempts remaining: {attempts}")

        if attempts == 0:
            print(f"💀 Game over! The word was '{word}'. Better luck next time!")

if __name__ == "__main__":
    hangman()
