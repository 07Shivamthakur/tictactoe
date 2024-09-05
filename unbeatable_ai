import math

# Initialize board
board = [' ' for _ in range(9)]  # Single list to simulate 3x3 grid

def print_board():
    for row in [board[i*3:(i+1)*3] for i in range(3)]:
        print('| ' + ' | '.join(row) + ' |')

def check_winner(player):
    win_conditions = [(0, 1, 2), (3, 4, 5), (6, 7, 8), (0, 3, 6), (1, 4, 7), (2, 5, 8), (0, 4, 8), (2, 4, 6)]
    return any(board[i] == board[j] == board[k] == player for i, j, k in win_conditions)

def check_tie():
    return ' ' not in board

# Player move
def player_move():
    while True:
        move = int(input('Enter your move (1-9): ')) - 1
        if board[move] == ' ':
            board[move] = 'X'
            break
        else:
            print('Invalid move, try again.')

# AI move using Minimax algorithm
def ai_move():
    best_score = -math.inf
    best_move = None

    for i in range(9):
        if board[i] == ' ':
            board[i] = 'O'  # Try the move
            score = minimax(board, 0, False)  # Simulate player's turn
            board[i] = ' '  # Undo the move
            if score > best_score:
                best_score = score
                best_move = i

    board[best_move] = 'O'

# Minimax algorithm
def minimax(board, depth, is_maximizing):
    if check_winner('O'):  # AI wins
        return 1
    elif check_winner('X'):  # Player wins
        return -1
    elif check_tie():  # Tie
        return 0

    if is_maximizing:  # AI's turn (Maximizing player)
        best_score = -math.inf
        for i in range(9):
            if board[i] == ' ':
                board[i] = 'O'  # AI plays here
                score = minimax(board, depth + 1, False)
                board[i] = ' '  # Undo the move
                best_score = max(score, best_score)
        return best_score
    else:  # Player's turn (Minimizing player)
        best_score = math.inf
        for i in range(9):
            if board[i] == ' ':
                board[i] = 'X'  # Player plays here
                score = minimax(board, depth + 1, True)
                board[i] = ' '  # Undo the move
                best_score = min(score, best_score)
        return best_score

# Main game loop
def tic_tac_toe():
    print("Welcome to Tic-Tac-Toe!")
    print_board()

    while True:
        player_move()
        print_board()
        if check_winner('X'):
            print('Congratulations, you win!')
            break
        if check_tie():
            print("It's a tie!")
            break

        ai_move()
        print('AI makes a move:')
        print_board()
        if check_winner('O'):
            print('AI wins!')
            break
        if check_tie():
            print("It's a tie!")
            break

tic_tac_toe()
