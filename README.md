# Games-public
I made a new game repository and made it public

# Create an empty board
board = [' ' for _ in range(9)]

# Print the board
def print_board():
    for i in range(3):
        print(board[i*3], '|', board[i*3 + 1], '|', board[i*3 + 2])
        if i < 2:
            print('---------')

# Game loop
player = 'X'
while True:
    print_board()
    position = int(input(f"Player {player}, choose a position (1-9): ")) - 1

    if board[position] == ' ':
        board[position] = player
    else:
        print("That position is already taken. Try again.")
        continue

    # Check for winning conditions
    if (
        (board[0] == board[1] == board[2] == player) or
        (board[3] == board[4] == board[5] == player) or
        (board[6] == board[7] == board[8] == player) or
        (board[0] == board[3] == board[6] == player) or
        (board[1] == board[4] == board[7] == player) or
        (board[2] == board[5] == board[8] == player) or
        (board[0] == board[4] == board[8] == player) or
        (board[2] == board[4] == board[6] == player)
    ):
        print_board()
        print(f"Player {player} wins!")
        break

    # Switch players
    player = 'O' if player == 'X' else 'X'