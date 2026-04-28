# 🚀 ZUNAIRA AHMED - ASSEMBLY & DATA STRUCTURES PROJECTS

<p align="center">
  <img src="https://img.shields.io/badge/Zunaira%20Ahmed-Computer%20Science-red?style=for-the-badge">
  <img src="https://img.shields.io/badge/FJWU-BSCS--III-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Section-B-brightgreen?style=for-the-badge">
</p>

---

## 👩‍💻 Author
**Zunaira Ahmed**  
*Computer Science Student | Developer | Problem Solver | Digital Logic Enthusiast*  
📞 Contact: +92 336 5690354  
✉️ Email: zunairaahmed1115@gmail.com  
📍 Location: Rawalpindi, Pakistan

---

## 📚 TABLE OF CONTENTS

| # | Project Name | Language/Technology |
|---|--------------|---------------------|
| 1 | Tic Tac Toe Game | C Language |
| 2 | Password Security System | 8086 Assembly |
| 3 | Knight's Travails | Java Swing |

---

# 🎮 PROJECT 1: TIC TAC TOE GAME IN C

![Language](https://img.shields.io/badge/Language-C-blue.svg)
![Version](https://img.shields.io/badge/Version-1.0-green.svg)
![Status](https://img.shields.io/badge/Status-Stable-brightgreen.svg)
![File Handling](https://img.shields.io/badge/File%20Handling-Included-orange.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

## 📖 INTRODUCTION

This program implements a simple Tic Tac Toe game in C, allowing two players to play interactively. The game is designed to log all moves made during the game to a text file and save the final result (including the final board and the winner or draw) to another text file. The program uses basic concepts such as arrays, file handling, and conditional logic to implement the game.

## 🎯 PROGRAM OVERVIEW

- **🎲 Game Objective:** The goal of the game is to place your symbol (X or O) in a 3x3 grid, and the first player to align three of their symbols in a row, column, or diagonal wins. If all cells are filled without a winner, the game results in a draw.

- **🔄 Game Flow:**
  - Players take turns to enter a move, which is a number between 1 and 9 that corresponds to an empty cell on the board.
  - The program checks whether a player has won or if the game is a draw after each move.
  - It logs each move to a file (`game_log.txt`) and saves the final game result to another file (`game_result.txt`).

- **📁 File Logging:**
  - Moves are logged to a file (`game_log.txt`) so that players can review the sequence of the game.
  - After the game ends, the final game state (board and result) is saved to a file (`game_result.txt`).

## 💻 CODE

```c
#include <stdio.h>
#include <stdlib.h>

void displayBoard(char *board);
int checkWinner(char *board);
void saveGame(char *board, const char *filename, const char *result);

int main() {
    char board[9] = {'1', '2', '3', '4', '5', '6', '7', '8', '9'};
    char *boardPtr = board; // Pointer to the board array
    int player = 1, choice, gameStatus = 0;
    char mark;
    FILE *file;
    
    file = fopen("game_log.txt", "w"); // Open file to log moves
    if (file == NULL) {
        printf("Error opening file!\n");
        return 1;
    }
    fprintf(file, "Tic Tac Toe Game Log:\n\n");
    fclose(file);
    
    while (gameStatus == 0) {
        displayBoard(boardPtr);
        player = (player % 2) ? 1 : 2;
        mark = (player == 1) ? 'X' : 'O';
        
        printf("Player %d, enter your choice: ", player);
        scanf("%d", &choice);
        
        if (choice >= 1 && choice <= 9 && board[choice - 1] == '1' + (choice - 1)) {
            board[choice - 1] = mark;
            
            // Log move to file
            file = fopen("game_log.txt", "a");
            fprintf(file, "Player %d placed %c at position %d\n", player, mark, choice);
            fclose(file);
        } else {
            printf("Invalid move! Try again.\n");
            player--;
        }
        
        gameStatus = checkWinner(boardPtr);
        player++;
    }
    
    displayBoard(boardPtr);
    
    if (gameStatus == 1) {
        printf("==> Player %d wins!\n", --player);
        saveGame(boardPtr, "game_result.txt", player == 1 ? "Player 1 (X) Wins!" : "Player 2 (O) Wins!");
    } else {
        printf("==> Game Draw!\n");
        saveGame(boardPtr, "game_result.txt", "Draw!");
    }
    
    return 0;
}

// Function to display the board
void displayBoard(char *board) {
    printf("\n");
    printf(" %c | %c | %c \n", board[0], board[1], board[2]);
    printf("---|---|---\n");
    printf(" %c | %c | %c \n", board[3], board[4], board[5]);
    printf("---|---|---\n");
    printf(" %c | %c | %c \n\n", board[6], board[7], board[8]);
}

// Function to check for a winner
int checkWinner(char *board) {
    // Check rows, columns, and diagonals
    for (int i = 0; i < 3; i++) {
        if (board[i] == board[i + 3] && board[i] == board[i + 6])
            return 1; // Columns
        if (board[i * 3] == board[i * 3 + 1] && board[i * 3] == board[i * 3 + 2])
            return 1; // Rows
    }
    if (board[0] == board[4] && board[0] == board[8])
        return 1; // Main diagonal
    if (board[2] == board[4] && board[2] == board[6])
        return 1; // Anti-diagonal
    
    // Check for a draw (no empty spaces)
    for (int i = 0; i < 9; i++) {
        if (board[i] != 'X' && board[i] != 'O')
            return 0;
    }
    return -1; // Draw
}

// Function to save the final board and result to a file
void saveGame(char *board, const char *filename, const char *result) {
    FILE *file = fopen(filename, "w");
    if (file == NULL) {
        printf("Error opening file for saving game result!\n");
        return;
    }
    fprintf(file, "Final Board:\n");
    fprintf(file, " %c | %c | %c \n", board[0], board[1], board[2]);
    fprintf(file, "---|---|---\n");
    fprintf(file, " %c | %c | %c \n", board[3], board[4], board[5]);
    fprintf(file, "---|---|---\n");
    fprintf(file, " %c | %c | %c \n\n", board[6], board[7], board[8]);
    fprintf(file, "Result: %s\n", result);
    fclose(file);
}
# 📖 Code Explanation

## 📚 Header Files

| Header | Purpose |
|--------|---------|
| `stdio.h` | Provides input/output functions (`printf`, `scanf`, `fopen`, `fprintf`, `fclose`) |
| `stdlib.h` | Included for general-purpose functions (though not directly used) |

---

## 🔧 Variables Used

| Variable | Type | Purpose |
|----------|------|---------|
| `board[9]` | `char` | 3x3 board representation with positions 1-9 |
| `boardPtr` | `char*` | Pointer to board array for function passing |
| `player` | `int` | Tracks current player (1 or 2) |
| `choice` | `int` | Stores player's move position |
| `gameStatus` | `int` | 0=ongoing, 1=winner, -1=draw |
| `mark` | `char` | Player symbol ('X' or 'O') |

---

## 🔄 Main Function Walkthrough

### 1️⃣ File Initialization
- Opens `game_log.txt` in write mode (`"w"`)
- Writes header and closes file
- Error handling if file cannot be opened

### 2️⃣ Game Loop
```c
while (gameStatus == 0) {
    displayBoard(boardPtr);
    player = (player % 2) ? 1 : 2;
    mark = (player == 1) ? 'X' : 'O';
    // ... move handling ...
}
3️⃣ Move Validation
✅ Checks if choice is between 1 and 9

✅ Checks if position is available (matches original number)

❌ Shows error message for invalid moves

4️⃣ Game Status Check
Calls checkWinner() after each move

Returns: 1 = winner, -1 = draw, 0 = continue

## 🛠️ Helper Functions

| Function | Description |
|----------|-------------|
| `displayBoard(char *board)` | Prints current board state with grid lines |
| `checkWinner(char *board)` | Checks rows, columns, diagonals for win/draw |
| `saveGame(char *board, const char *filename, const char *result)` | Saves final board and result to file |

---

## 🎮 How It Works

### Step 1: Initialization 🚀
The board is set up with initial values (`'1'` to `'9'`). The game is ready to begin.

### Step 2: Player Moves 👥
Players take turns entering their moves. Each move is validated and then logged to a file.

**Move Log Format (`game_log.txt`):**

```text
Tic Tac Toe Game Log:

Player 1 placed X at position 5
Player 2 placed O at position 1
Player 1 placed X at position 9
Player 2 placed O at position 3
Player 1 placed X at position 7
Player 2 placed O at position 2

**Move Log Format (`game_log.txt`):**

Tic Tac Toe Game Log:

Player 1 placed X at position 5
Player 2 placed O at position 1
Player 1 placed X at position 9
...
Step 3: Check for Winner/Draw 🔍
After every move, the game checks if a player has won or if the game is a draw. If the game is ongoing, the turn alternates between players.

Step 4: End of Game 🏁
When a winner is found or all spaces are filled (draw), the game ends, the final board is displayed, and the result is saved to a file.

Result File Format (game_result.txt):

Final Board:
 X | O | X
---|---|---
 O | X | O
---|---|---
 7 | X | 9

Result: Player 1 (X) Wins!
🖼️ Sample Output
text
 1 | 2 | 3 
---|---|---
 4 | 5 | 6 
---|---|---
 7 | 8 | 9 

Player 1, enter your choice: 5

 1 | 2 | 3 
---|---|---
 4 | X | 6 
---|---|---
 7 | 8 | 9 

Player 2, enter your choice: 1

 O | 2 | 3 
---|---|---
 4 | X | 6 
---|---|---
 7 | 8 | 9 

Player 1, enter your choice: 9

 O | 2 | 3 
---|---|---
 4 | X | 6 
---|---|---
 7 | 8 | X 

Player 2, enter your choice: 3

 O | 2 | O 
---|---|---
 4 | X | 6 
---|---|---
 7 | 8 | X 

Player 1, enter your choice: 7

 O | 2 | O 
---|---|---
 4 | X | 6 
---|---|---
 X | 8 | X 

Player 2, enter your choice: 2

 O | O | O 
---|---|---
 4 | X | 6 
---|---|---
 X | 8 | X 

==> Player 2 wins!
🛠️ Technologies Used
<p align="center"> <img src="https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white"> <img src="https://img.shields.io/badge/GCC-5C6BC0?style=for-the-badge&logo=gnu&logoColor=white"> <img src="https://img.shields.io/badge/VS%20Code-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white"> </p> ```

---
## 📚 Concepts Used

- ✅ **Arrays** - Board representation
- ✅ **Pointers** - Efficient array manipulation
- ✅ **File Handling** - Move logging and result saving
- ✅ **Conditional Logic** - Win/draw detection
- ✅ **Loops** - Game flow control (`while`, `for`)
- ✅ **Functions** - Modular code organization

---

## 💻 How to Run

### 🐧 On Linux/Mac Terminal:
```bash
# Compile the program
gcc tictactoe.c -o tictactoe

# Run the executable
./tictactoe

---

## 📝 Using any C IDE:
🔵 Code::Blocks

🔴 Dev-C++

🟣 Visual Studio

🟢 CLion

🟠 Eclipse CDT
---

## 📁 Files Generated
File Name	Description	Mode
game_log.txt	Logs each move made during the game	Append (a)
game_result.txt	Saves final board and game result	Write (w)
---

## ⚠️ Limitations
Limitation	          | Description
🔴 No input validation	  |Non-numeric entries cause crashes
🔴 No replay option	  |Cannot restart without recompiling
🔴 Single session	  |Only one game per execution
🔴 Text-based only	  |No GUI interface
🔴 Memory-based positions|	Players must remember position numbers

---

## 🚀 Future Enhancements
Enhancement	                         Status
🎮 Play against computer (AI)       	⏳ Planned
💾 Save/Load game feature		⏳ Planned
📊 Display move history from log	⏳ Planned
🎨 Colored output for better visibility	⏳ Planned
👥 Player name input	                ⏳ Planned
🔁 Replay option after game ends	⏳ Planned
🐛 Fix non-numeric input handling	⏳ Planned
📈 Win/loss statistics tracking		⏳ Planned
---

## 📈 Learning Outcomes
After completing this project, you will understand:

🧩 2D Board Representation using 1D arrays

📂 File Handling Operations (read, write, append)

🎯 Game Logic Implementation for win/draw conditions

🔗 Pointer Usage for array manipulation

🔄 Turn-based Game Loop design

📦 Modular Programming with functions

---

## ⭐ Show Your Support
<p align="center"> <a href="#"><img src="https://img.shields.io/badge/Star-⭐-yellow?style=for-the-badge"></a> <a href="#"><img src="https://img.shields.io/badge/Fork-⑂-blue?style=for-the-badge"></a> <a href="#"><img src="https://img.shields.io/badge/Follow-👥-green?style=for-the-badge"></a> </p>

---

## 📝 License

MIT License

Copyright (c) 2024 Tic Tac Toe Project

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files...
This project is created for educational purposes as part of coursework.
---
## 📞 Contact & Contributions
Feel free to fork this repository, submit issues, or contribute to future enhancements!
