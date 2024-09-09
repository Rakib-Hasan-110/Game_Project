#include <iostream>
using namespace std;

class TicTacToe {
private:
    char board[3][3];
    char current_marker;
    int current_player;

public:
    TicTacToe() {
        char ch = '1';
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                board[i][j] = ch++;
            }
        }
        current_player = 1;
    }

    void printBoard() {
        cout << " " << board[0][0] << " | " << board[0][1] << " | " << board[0][2] << endl;
        cout << "---|---|---" << endl;
        cout << " " << board[1][0] << " | " << board[1][1] << " | " << board[1][2] << endl;
        cout << "---|---|---" << endl;
        cout << " " << board[2][0] << " | " << board[2][1] << " | " << board[2][2] << endl;
    }

    bool placeMarker(int slot) {
        int row = (slot - 1) / 3;
        int col = (slot - 1) % 3;

        if (board[row][col] != 'X' && board[row][col] != 'O') {
            board[row][col] = current_marker;
            return true;
        } else {
            return false;
        }
    }

    int checkWinner() {
        for (int i = 0; i < 3; i++) {
            if (board[i][0] == board[i][1] && board[i][1] == board[i][2]) {
                return current_player;
            }
        }

        for (int i = 0; i < 3; i++) {
            if (board[0][i] == board[1][i] && board[1][i] == board[2][i]) {
                return current_player;
            }
        }

        if (board[0][0] == board[1][1] && board[1][1] == board[2][2]) {
            return current_player;
        }
        if (board[0][2] == board[1][1] && board[1][1] == board[2][0]) {
            return current_player;
        }

        return 0;
    }

    void swapPlayerAndMarker() {
        if (current_marker == 'X') {
            current_marker = 'O';
        } else {
            current_marker = 'X';
        }

        if (current_player == 1) {
            current_player = 2;
        } else {
            current_player = 1;
        }
    }

    void startGame() {
        cout << "Player 1, choose your marker (X or O): ";
        char marker_p1;
        cin >> marker_p1;

        current_marker = marker_p1;
        if (marker_p1 == 'X') {
            current_marker = 'X';
        } else {
            current_marker = 'O';
        }

        int winner = 0;
        int slot;
        for (int i = 0; i < 9; i++) {
            printBoard();
            cout << "Player " << current_player << ", choose a slot (1-9): ";
            cin >> slot;

            if (slot < 1 || slot > 9 || !placeMarker(slot)) {
                cout << "Invalid move! Try again.\n";
                i--;
                continue;
            }

            winner = checkWinner();
            if (winner != 0) {
                printBoard();
                cout << "Player " << winner << " wins!\n";
                break;
            }

            swapPlayerAndMarker();
        }

        if (winner == 0) {
            cout << "It's a draw!\n";
        }
    }
};

int main() {
    TicTacToe game;
    game.startGame();
    return 0;
}
