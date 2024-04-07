#include <iostream>
#include <vector>
#include <string>

using namespace std;

// Function prototypes
void display_board(const vector<vector<char>>& board);
bool check_win(const vector<vector<char>>& board, char player);
bool check_draw(const vector<vector<char>>& board);
void switch_player(char& current_player);

int main() {
    vector<vector<char>> board(3, vector<char>(3, ' ')); // Initialize the board with empty spaces
    char current_player = 'X'; // Player X starts the game

    bool game_over = false;
    while (!game_over) {
        // Display the current state of the board
        display_board(board);

        // Prompt the current player to enter their move
        int row, col;
        cout << "Player " << current_player << "'s turn. Enter row (0-2) and column (0-2): ";
        cin >> row >> col;

        // Update the game board with the player's move
        if (row >= 0 && row < 3 && col >= 0 && col < 3 && board[row][col] == ' ') {
            board[row][col] = current_player;

            // Check for win
            if (check_win(board, current_player)) {
                display_board(board);
                cout << "Player " << current_player << " wins!" << endl;
                game_over = true;
            }
            // Check for draw
            else if (check_draw(board)) {
                display_board(board);
                cout << "It's a draw!" << endl;
                game_over = true;
            }
            // Switch players
            else {
                switch_player(current_player);
            }
        } else {
            cout << "Invalid move. Try again." << endl;
        }
    }

    return 0;
}

// Function to display the current state of the board
void display_board(const vector<vector<char>>& board) {
    cout << "-------------" << endl;
    for (const auto& row : board) {
        cout << "| ";
        for (char cell : row) {
            cout << cell << " | ";
        }
        cout << endl << "-------------" << endl;
    }
}

// Function to check if the current player has won
bool check_win(const vector<vector<char>>& board, char player) {
    // Check rows and columns
    for (int i = 0; i < 3; ++i) {
        if ((board[i][0] == player && board[i][1] == player && board[i][2] == player) ||
            (board[0][i] == player && board[1][i] == player && board[2][i] == player)) {
            return true;
        }
    }
    // Check diagonals
    if ((board[0][0] == player && board[1][1] == player && board[2][2] == player) ||
        (board[0][2] == player && board[1][1] == player && board[2][0] == player)) {
        return true;
    }
    return false;
}

// Function to check if the game is a draw
bool check_draw(const vector<vector<char>>& board) {
    for (const auto& row : board) {
        for (char cell : row) {
            if (cell == ' ') {
                return false; // Empty cell found, game is not a draw
            }
        }
    }
    return true; // All cells are filled, game is a draw
}

// Function to switch players
void switch_player(char& current_player) {
    current_player = (current_player == 'X') ? 'O' : 'X';
}
