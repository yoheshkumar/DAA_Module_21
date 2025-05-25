# EX 3C Sudoku Solver
## DATE:
## AIM:
To write a python program to find the solution of sudoku puzzle using Backtracking.


## Algorithm:

1. **Find the First Empty Cell:**  
   - Iterate over each cell in the 9x9 board.  
   - If an empty cell (value `0`) is found, proceed to the next step.  

2. **Try Possible Values (1-9):**  
   - For each empty cell, try placing digits from `1` to `9`.  
   - Use the `isPossible()` function to check if a given value is valid for the current cell:  
     - **Row Check:** Ensure the value doesn't already exist in the current row.  
     - **Column Check:** Ensure the value doesn't already exist in the current column.  
     - **Subgrid Check:** Ensure the value doesn't already exist in the 3x3 subgrid containing the cell.  

3. **Recursive Backtracking:**  
   - If a valid value is found:  
     - Place the value in the cell.  
     - Recursively attempt to solve the rest of the board.  
   - If no valid number can be placed in the current cell, reset it to `0` (backtrack) and try the next possible value.  

4. **Print the Solution:**  
   - If the board is completely filled (no empty cells remain), print the solved board.  

5. **End the Recursion:**  
   - Once a valid solution is found and printed, terminate further recursive calls to avoid printing multiple solutions.  

## Program:
```
/*
Program to implement to to find the solution of sudoku puzzle using Backtracking.

Developed by: YOHESH KUMAR R.M
Register Number: 212222240118
*/

board = [
    [0, 0, 0, 8, 0, 0, 4, 0, 3],
    [2, 0, 0, 0, 0, 4, 8, 9, 0],
    [0, 9, 0, 0, 0, 0, 0, 0, 2],
    [0, 0, 0, 0, 2, 9, 0, 1, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 7, 0, 6, 5, 0, 0, 0, 0],
    [9, 0, 0, 0, 0, 0, 0, 8, 0],
    [0, 6, 2, 7, 0, 0, 0, 0, 1],
    [4, 0, 3, 0, 0, 6, 0, 0, 0]
]

def printBoard(board):
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(board, row, col, val):
    for j in range(0, 9):
        if board[row][j] == val:
            return False

    for i in range(0, 9):
        if board[i][col] == val:
            return False

    startRow = (row // 3) * 3
    startCol = (col // 3) * 3
    for i in range(0, 3):
        for j in range(0, 3):
            if board[startRow+i][startCol+j] == val:
                return False
    return True

def solve():
    for i in range(0, 9):
        for j in range(0, 9):
            if board[i][j] == 0:
                for val in range(1, 10):
                    if isPossible(board, i, j, val):
                        board[i][j] = val
                        solve()
                        board[i][j] = 0
                return
    printBoard(board)
solve()
```

## Output:

![image](https://github.com/user-attachments/assets/53741ee3-cc9b-4a2d-9558-7856c798f2bf)

## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.
