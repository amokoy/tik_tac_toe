# tik_tac_toe
tik-tok game

# the first part of the code 
## print the game board
def print_board(board):
    """
    Print the game board.
    """
    for row in board:
        print(' | '.join(row))
        print('---------')


# the second part of the code
## take player input
def take_player_input(board, player):
    """
    Take player input and update the game board.
    """
    position = input("Player " + player + ", enter your move (1-9): ")
    # Update the corresponding position on the board with the player's symbol
    # Here, assuming the board is a 2D list of strings
    board[(position - 1) // 3][(position - 1) % 3] = player

# the third part of the code 
## check for win and tie 
def check_win(board, player):
    """
    Check if the current player has won the game.
    """
    # Check rows
    for row in board:
        if row.count(player) == 3:
            return True
    # Check columns
    for col in range(3):
        if board[0][col] == board[1][col] == board[2][col] == player:
            return True
    # Check diagonals
    if board[0][0] == board[1][1] == board[2][2] == player or board[0][2] == board[1][1] == board[2][0] == player:
        return True
    return False

# the fourth part of the code 
## check if there is a ties
def check_tie(board):
    """
    Check if the game has ended in a tie.
    """
    for row in board:
        if ' ' in row:
            return False
    return True

# the fifth part of code
## switches players 
def switch_player(player):
    """
    Switch the current player.
    """
    if player == 'X':
        return 'O'
    else:
        return 'X'

# the sith part of the code 
## ai appoinnent
def play_against_ai():
    """
    Play against an AI opponent.
    """
    board = [[' ', ' ', ' '], [' ', ' ', ' '], [' ', ' ', ' ']]
    player = 'X'
    while True:
        print_board(board)
        take_player_input(board, player)
        if check_win(board, player):
            print("Player " + player + " wins!")
            break
        elif check_tie(board):
            print("It's a tie!")
            break
        player = switch_player(player)

    # AI's turn (example: random move)
    ai_move = random.choice(range(1, 10))
    board[(ai_move - 1) // 3][(ai_move - 1) % 3] = 'O'

    print_board(board)
    if check_win(board, 'O'):
        print("AI wins!")
    elif check_tie(board):
        print("It's a tie!")

play_against_ai()
