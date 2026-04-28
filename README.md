
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
