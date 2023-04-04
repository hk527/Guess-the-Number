[Guess the Number Explanation.pdf](https://github.com/hk527/Guess-the-Number/files/11153843/Guess.the.Number.Explanation.pdf)
# Guess-the-Number
Guess the Number Game
Number Guessing Game
import random
import time
import winsound

def play_game():
    print("Welcome to the number guessing game!")
    time.sleep(1)
    name = input("What is your name? ")
    print("Hello, " + name + "! Let's get started.")
    time.sleep(1)
    high_score = None
    while True:
        num = random.randint(1, 100)
        print("I'm thinking of a number between 1 and 100.")
        time.sleep(1)
        start_time = time.time()
        num_guesses = 0
        while True:
            guess = input("What is your guess? ")
            if guess.lower() == "quit":
                print("Thanks for playing!")
                return
            try:
                guess = int(guess)
            except ValueError:
                print("Invalid input. Please enter a number between 1 and 100.")
                continue
            num_guesses += 1
            if guess < num:
                print("Too low!")
                winsound.PlaySound("SystemQuestion", winsound.SND_ALIAS)
            elif guess > num:
                print("Too high!")
                winsound.PlaySound("SystemHand", winsound.SND_ALIAS)
            else:
                end_time = time.time()
                time_taken = round(end_time - start_time, 2)
                print("Congratulations, " + name + "! You guessed the number in " + str(num_guesses) + " guesses in " + str(time_taken) + " seconds.")
                if high_score is None or num_guesses < high_score:
                    high_score = num_guesses
                    print("Congratulations, " + name + "! You set a new high score of " + str(high_score) + "!")
                    winsound.PlaySound("SystemAsterisk", winsound.SND_ALIAS)
                else:
                    print("The current high score is " + str(high_score) + ".")
                break

play_game()
