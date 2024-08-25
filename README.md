# ♔ N-Queens Visualizer

## 📖 Introduction
The **N-Queens Visualizer** is an interactive web-based tool designed to help users visualize solutions to the classic N-Queens problem. The N-Queens problem challenges you to place N queens on an N×N chessboard such that no two queens threaten each other. This tool enables you to explore and understand the various configurations that solve the problem.

## ✨ Features
- 🎥 **Interactive Visualization**: Watch the N-Queens problem unfold on a responsive chessboard.
- 📏 **Customizable Board Size**: Input the number of queens (from 1 to 8) to visualize different solutions.
- 🎚️ **Slider Control**: Adjust the speed of the visualization using a slider.
- 📱 **Responsive Design**: The interface is optimized for various screen sizes and devices.
- 📝 **Detailed Output**: Displays the number of possible arrangements and visualizes each solution step-by-step.

## ⚙️ Installation
To run this project locally, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/SaiSriramKamineni/N-Queen-Visualizer.git
    ```

2. Navigate to the project directory:
    ```bash
    cd n-queens-visualizer
    ```

3. Open `index.html` in your preferred web browser.

## 🚀 Usage
1. Open the `index.html` file in your web browser.
2. Enter the number of queens in the input box (1-8).
3. Use the slider to adjust the speed of the visualization.
4. Click the "Play" button to start the visualization.

The chessboard will display all the possible solutions for the given number of queens. The queens will be placed on the board one by one, following the rules of the N-Queens problem.

## 💻 Technologies Used
- 🌐 **HTML**: Structure of the web page.
- 🎨 **CSS**: Styling and layout.
- ⚙️ **JavaScript**: Logic and interactivity of the visualization.
## 🤝 Contributing
Contributions are welcome! If you have suggestions for improving the visualizer, feel free to create an issue or submit a pull request. Let's make this tool even better together! 💡

Happy coding! 🎉

## 📄 Code Examples
### C++
```cpp
#include <iostream>
#include <vector>
using namespace std;

class NQueens {
public:
    NQueens(int n) : N(n), board(n, vector<bool>(n, false)) {
        solve(0);
    }
    
    void printSolutions() {
        for (const auto& solution : solutions) {
            for (const auto& row : solution) {
                for (bool cell : row) {
                    cout << (cell ? "Q " : ". ");
                }
                cout << endl;
            }
            cout << endl;
        }
    }
    
private:
    int N;
    vector<vector<bool>> board;
    vector<vector<vector<bool>>> solutions;

    void solve(int row) {
        if (row == N) {
            solutions.push_back(board);
            return;
        }
        for (int col = 0; col < N; ++col) {
            if (isValid(row, col)) {
                board[row][col] = true;
                solve(row + 1);
                board[row][col] = false;
            }
        }
    }

    bool isValid(int row, int col) {
        for (int i = 0; i < row; ++i) {
            if (board[i][col] || 
                (col - (row - i) >= 0 && board[i][col - (row - i)]) || 
                (col + (row - i) < N && board[i][col + (row - i)])) {
                return false;
            }
        }
        return true;
    }
};

int main() {
    int n = 8;
    NQueens nQueens(n);
    nQueens.printSolutions();
    return 0;
}
