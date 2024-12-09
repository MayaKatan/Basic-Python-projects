"""
@Project: Maman11
@Description: This project contains solutions to 4 programming tasks based on the concepts learned in units 1-4 of the course.
Each task focuses on a specific topic:
1. Rock-Paper-Scissors tournament simulation.
2. Validation of an Israeli ID number with supporting utility functions.
3. Calculation of the largest common prime divisor between two numbers.
4. Identification and listing of perfect numbers up to a given number.

@Author: Maya_Katan
@Semester: 2025a
"""

# Question 1: Rock-Paper-Scissors Tournament
def game (player1,player2):
    """
    Determines the winner of a single round in a Rock-Paper-Scissors game.

    Args:
        player1 (str): The choice of the first player ('R' for Rock, 'P' for Paper, 'S' for Scissors).
        player2 (str): The choice of the second player ('R' for Rock, 'P' for Paper, 'S' for Scissors).

    Returns:
        int:
            0 if the round ends in a tie.
            1 if Player 1 wins.
            2 if Player 2 wins.
    """
    if player1 == player2:
        return 0 #a tie
    elif (player1 == 'R' and player2 =='S') or \
         (player1 == 'S' and player2 =='P') or \
         (player1 == 'P' and player2 =='R'):
        return 1 #Player1 is the winner
    else:
        return 2 #Player2 is the winner

def tournament ():
    """
    Manages a Rock-Paper-Scissors tournament between two players.
    Each tournament consists of up to 5 rounds, and the first player to win 3 rounds is declared the winner.

    Prompts:
        Prompts both players to input their names and their choices for each round.
        Displays the winner of each round and the overall tournament winner.
    """
    player1_name = input("Please enter first player name:")
    player2_name = input("Please enter second player name:")

    player1_wins = 0
    player2_wins = 0
    current_round = 1

    while current_round <= 5 and player1_wins < 3 and player2_wins < 3:
        player1_choice = input("First player, please enter your choice:")
        player2_choice = input("Second player, please enter your choice:")

        winner = game(player1_choice, player2_choice)

        if winner == 1:
            print (f"Round {current_round} winner: {player1_name}")
            player1_wins += 1
        elif winner == 2:
            print (f"Round {current_round} winner: {player2_name}")
            player2_wins += 1
        else:
            print(f"Round {current_round} resulted in a tie")

        current_round += 1

    if player1_wins > player2_wins:
        print(f"Congratulations {player1_name}! You are the winner of the tournament!")
    elif player1_wins < player2_wins:
        print(f"Congratulations {player2_name}! You are the winner of the tournament!")
    else:
        print ("The tournament ended in a tie, thank you for playing!")



# Question 2: Validation of an Israeli ID Number
def sum_digits(num):
    """
    Calculates the sum of the digits of a two-digit number.

    Args:
        num (int): A two-digit integer.
    Returns:
        int: The sum of the tens digit and the units digit.
    """
    current = num
    result = 0
    if num < 10:
        return num
    else:
        while current != 0:
            result += current % 10
            current = current // 10
        return result

def close_to_ten(num):
    """
    Rounds a number up to the nearest multiple of 10 if it's not already a multiple of 10.

    Args:
        num (int): An integer to round.
    Returns:
        int: The nearest multiple of 10 greater than or equal to the input.
    """
    if num % 10 <= 0:
        return num
    else:
        return num + 10 - (num % 10)

def valid_id(num_id):
    """
    Validates an Israeli ID number.

    Args:
        num_id (str): A string representing the ID number.
    Returns:
        str:
            "ERROR" if the input is invalid (not 9 characters long or contains non-digit characters).
            "OK" if the ID number passes all validation checks.
    """

    num = 0
    if len(num_id) != 9 or not num_id.isdigit():  # Check if the input is of the requested length,  Return an error if a condition is incorrect
        print("ERROR")
    else:
        for i in range(8):  # Check that each character is a digit
            if i % 2 == 0:
                num += sum_digits(int(num_id[i]) * 1)
            else:
                num += sum_digits(int(num_id[i]) * 2)
        num = close_to_ten(num) - num
        if num == int(num_id[-1]):
            print("OK")  # Return OK if all checks pass
        else:
            print("ERROR")



# Question 3: Largest Common Prime Divisor
def max_prime_divider(n):
    """
    Finds the largest prime factor of a given number.

    Args:
        n (int): The number for which the largest prime factor is to be found.

    Returns:
        int: The largest prime factor of the number.
    """
    i, current = 2, 2
    prime_num = True
    while i <= n:
        if n % i == 0:
            for j in range(2, int(i**0.5)+1):
                if i % j == 0:
                    prime_num = False
                    break
            if prime_num:
                current = i
        i = i + 1
    return current

def max_common_prime_divider(n1, n2):
    """
    Finds the largest common prime divisor between two numbers.

    Args:
        n1 (int): The first number.
        n2 (int): The second number.

    Returns:
        int: The largest common prime divisor between n1 and n2. If none exist, returns 1.
    """
    max_divisor_n1 = max_prime_divider(n1)
    max_divisor_n2 = max_prime_divider(n2)

    largest_common_divisor = 1  # The initial common divisor of every number

    ## Check if the prime divisor of n1 is shared with n2 and n3
    if max_divisor_n1 and n2 % max_divisor_n1 == 0:
        largest_common_divisor = max(largest_common_divisor, max_divisor_n1)

    ## Check if the prime divisor of n2 is shared with n1 and n3
    if max_divisor_n2 and n1 % max_divisor_n2 == 0:
        largest_common_divisor = max(largest_common_divisor, max_divisor_n2)

    return largest_common_divisor



# Question 4: Perfect Numbers
def is_perfect(n):
    """
    Checks if a number is a perfect number.

    A perfect number is a positive integer that is equal to the sum of its proper divisors
    (excluding itself).

    Args:
        n (int): The number to check.
    Returns:
        bool: True if the number is a perfect number, False otherwise.
    """
    cumulative_sum = 0

    for i in range(1, n):
        if n % i == 0:
            cumulative_sum += i
    return cumulative_sum == n

def perfect_numbers(num):
    """
    Finds and prints all perfect numbers up to a given number.

    A perfect number is a positive integer that is equal to the sum of its proper divisors
    (excluding itself). If no perfect numbers exist in the range, it notifies the user.

    Args:
        num (int): The upper limit (inclusive) to check for perfect numbers.
    """
    count = 0

    for i in range(1, num +1):
        if is_perfect(i):
            if count > 0:
                print(", ", end="")
            print(i, end="")
            count += 1

    if count == 0 :
        print("There are no perfect numbers.")
    else:
        print()
