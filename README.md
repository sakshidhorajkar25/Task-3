import random
# Word list for the game
words = ['python', 'hangman', 'programming', 'code', 'developer']

# Pick a random word
word = random.choice(words)
guessed = ['_'] * len(word)
attempts = 6
guessed_letters = []

print("Welcome to Hangman!")
print("Guess the word:", ' '.join(guessed))

while attempts > 0 and '_' in guessed:
    guess = input("Enter a letter: ").lower()

    if not guess.isalpha() or len(guess) != 1:
        print("Please enter a single valid letter.")
        continue

    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue
 guessed_letters.append(guess)

    if guess in word:
        for i, letter in enumerate(word):
            if letter == guess:
                guessed[i] = guess
        print("Good guess:", ' '.join(guessed))
    else:
        attempts -= 1
        print(f"Wrong! Attempts left: {attempts}")
        print(' '.join(guessed))

if '_' not in guessed:
    print("Congratulations! You guessed the word:", word)
else:
    print("Game Over! The word was:", word)
