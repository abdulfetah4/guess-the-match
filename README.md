# guess-the-matchimport random

def generate_match_result():
    results = ['win', 'lose', 'draw']
    return random.choice(results)

def play_game():
    total_reward = 0
    hearts = 3  # Initial number of hearts
    cost_per_heart = 1
    rounds = 5  # Number of rounds to play

    print("Welcome to the 'Guess the Football Match' game!")
    print("Try to guess if the match will end in a 'win', 'lose', or 'draw'.")
    print(f"You start with {hearts} hearts (chances).")
    
    for i in range(rounds):
        if hearts <= 0:
            print("You have run out of hearts. Game over!")
            break

        print(f"\nYou have {hearts} hearts remaining.")
        action = input("Would you like to play a round or buy an additional heart? (play/buy): ").strip().lower()

        if action == 'buy':
            total_reward -= cost_per_heart
            hearts += 1
            print(f"Heart purchased! You now have {hearts} hearts. Your total reward is ${total_reward}.")
            continue
        elif action != 'play':
            print("Invalid action. Please enter 'play' or 'buy'.")
            continue

        match_result = generate_match_result()
        user_guess = input(f"Round {i + 1}: Enter your guess ('win', 'lose', or 'draw'): ").strip().lower()

        if user_guess not in ['win', 'lose', 'draw']:
            print("Invalid guess. Please enter 'win', 'lose', or 'draw'.")
            continue

        if user_guess == match_result:
            print(f"Congratulations! You guessed right. The match ended in a {match_result}.")
            total_reward += 1
        else:
            print(f"Sorry, you guessed wrong. The match ended in a {match_result}.")
            hearts -= 1

    print(f"\nGame over! You guessed correctly {total_reward} times.")
    print(f"Your final reward is ${total_reward}.")
    print(f"You ended with {hearts} hearts.")

if __name__ == "__main__":
    play_game()
