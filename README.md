 python-programming-internship
internship at cipherbyte technology
task 1: mastermind game
import random

def generate_code(length=4, colors=6):
    """Generate a random code."""
    return [random.randint(0, colors - 1) for _ in range(length)]

def get_feedback(guess, code):
    """Get feedback on the guess compared to the code."""
    correct_position = sum(g == c for g, c in zip(guess, code))
    correct_color = sum(min(guess.count(c), code.count(c)) for c in set(guess)) - correct_position
    return correct_position, correct_color

def print_code(code):
    """Print the code in a readable format."""
    print(" ".join(map(str, code)))

def main():
    length = 4  # Length of the code
    colors = 6  # Number of colors
    max_attempts = 10  # Maximum number of attempts

    print(f"Welcome to Mastermind!")
    print(f"I have selected a code of length {length} with {colors} colors.")
    print(f"Try to guess the code. You have {max_attempts} attempts.")

    code = generate_code(length, colors)
    attempts = 0

    while attempts < max_attempts:
        guess = input(f"Attempt {attempts + 1}: Enter your guess (space-separated numbers between 0 and {colors - 1}): ")
        guess = list(map(int, guess.split()))

        if len(guess) != length or any(g < 0 or g >= colors for g in guess):
            print("Invalid guess. Please enter the correct number of colors.")
            continue

        correct_position, correct_color = get_feedback(guess, code)
        print(f"Correct colors in the correct position: {correct_position}")
        print(f"Correct colors but in the wrong position: {correct_color}")

        if correct_position == length:
            print("Congratulations! You've guessed the code!")
            break

        attempts += 1

    if correct_position != length:
        print("Sorry, you've run out of attempts. The code was:", end=" ")
        print_code(code)

if __name__ == "__main__":
    main()
    task2:import random

def generate_code(length=4, colors=6):
    """Generate a random code."""
    return [random.randint(0, colors - 1) for _ in range(length)]

def get_feedback(guess, code):
    """Get feedback on the guess compared to the code."""
    correct_position = sum(g == c for g, c in zip(guess, code))
    correct_color = sum(min(guess.count(c), code.count(c)) for c in set(guess)) - correct_position
    return correct_position, correct_color

def print_code(code):
    """Print the code in a readable format."""
    print(" ".join(map(str, code)))

def main():
    length = 4  # Length of the code
    colors = 6  # Number of colors
    max_attempts = 10  # Maximum number of attempts

    print(f"Welcome to Mastermind!")
    print(f"I have selected a code of length {length} with {colors} colors.")
    print(f"Try to guess the code. You have {max_attempts} attempts.")

    code = generate_code(length, colors)
    attempts = 0

    while attempts < max_attempts:
        guess = input(f"Attempt {attempts + 1}: Enter your guess (space-separated numbers between 0 and {colors - 1}): ")
        guess = list(map(int, guess.split()))

        if len(guess) != length or any(g < 0 or g >= colors for g in guess):
            print("Invalid guess. Please enter the correct number of colors.")
            continue

        correct_position, correct_color = get_feedback(guess, code)
        print(f"Correct colors in the correct position: {correct_position}")
        print(f"Correct colors but in the wrong position: {correct_color}")

        if correct_position == length:
            print("Congratulations! You've guessed the code!")
            break

        attempts += 1

    if correct_position != length:
        print("Sorry, you've run out of attempts. The code was:", end=" ")
        print_code(code)

if __name__ == "__main__":
    main()
task 2: paper and scissor game
import random

def get_computer_choice():
    """Randomly select a choice for the computer."""
    choices = ["rock", "paper", "scissors"]
    return random.choice(choices)

def get_user_choice():
    """Get the user's choice."""
    while True:
        choice = input("Enter your choice (rock, paper, or scissors): ").lower()
        if choice in ["rock", "paper", "scissors"]:
            return choice
        else:
            print("Invalid choice. Please choose 'rock', 'paper', or 'scissors'.")

def determine_winner(user_choice, computer_choice):
    """Determine the winner of the game."""
    if user_choice == computer_choice:
        return "It's a tie!"
    elif (user_choice == "rock" and computer_choice == "scissors") or \
         (user_choice == "scissors" and computer_choice == "paper") or \
         (user_choice == "paper" and computer_choice == "rock"):
        return "You win!"
    else:
        return "You lose!"

def play_game():
    """Play a single game of Rock, Paper, Scissors."""
    print("Welcome to Rock, Paper, Scissors!")
    user_choice = get_user_choice()
    computer_choice = get_computer_choice()
    
    print(f"\nYou chose: {user_choice}")
    print(f"The computer chose: {computer_choice}")
    
    result = determine_winner(user_choice, computer_choice)
    print(result)

if __name__ == "__main__":
    play_game()

