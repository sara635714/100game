/*Program: Description of the program this game is a two players game they start from the point 0
 * and each of them will take turns adding a number from 1 to 10 and the one who reaches 100 fist is the winner
 * Game : game1(100game)
 * author : sara ibrahim mohamed
 * ID :20230166
 * version : 1.0
 * Date : 29/2/2024 */


#include <iostream>
#include <limits>

using namespace std;

int main() {
    int total_sum = 0;
    int num;
    int currentPlayer = 1;   // Current player (1 or 2)

    // Display welcome message and game rules
    cout << "Welcome to 100 game" << endl;
    cout << "Starting point is " << total_sum << endl;
    cout << "The winner is the one who reaches 100 first" << endl;
    // Main game loop
    while (total_sum < 100) {
        // Check if the total sum is close to 100
        if (total_sum >= 90) {
            // Calculate remaining points needed to reach 100
            int rem = 100 - total_sum;
            //loop for input validation
            while (true) {
                cout << "Player " << currentPlayer << " please enter a number from 1 to " << rem << endl;
                cin >> num;

                // Input validation
                if (cin.fail() || num < 1 || num > rem) {
                    cin.clear();
                    cin.ignore(numeric_limits<streamsize>::max(), '\n');
                    cout << "Invalid input" << endl;
                    continue;
                }
                else {
                    // Update total sum and check for a winner
                    total_sum += num;
                    cout << "Now we have " << total_sum << endl;
                    if (total_sum == 100) {
                        cout << "The sum has reached 100 " << endl;
                        cout << "Player " << currentPlayer << " wins" << endl;
                        cout << "Game over" << endl;
                        break;
                    }
                }
            }
        }
        else {
            // Prompt the current player to enter a number between 1 and 10
            cout << "Player " << currentPlayer << " Please enter a number from 1 to 10" << endl;
            cin >> num;

            //validation
            if (cin.fail() || num < 1 || num > 10) {
                cin.clear();
                cin.ignore(numeric_limits<streamsize>::max(), '\n');
                cout << "Invalid input" << endl;
                continue;
            }
            else {
                // Update total sum and switch to the other player
                total_sum += num;
                cout << "Now we have " << total_sum << endl;
                currentPlayer = (currentPlayer == 1) ? 2 : 1;
            }
        }
    }

    return 0;
}
