----------------
SudokuSolver.py
----------------

Hello! Welcome to my Sudoku solver which has been designed from scratch and implemented in python. The search algorithm used is Depth-First-Search (Brute-Force).
There are 4 preset boards that I have given with the application: board1(), board2(), board3(), board4().

-----------
Execution
-----------

To run any of the 4 preset boards, after the module has been run from Python's GUI (IDLE).

   dfs(BOARD_OBJECT) - dfs requires a board object to be passed in

Example: dfs(board3())

-------------------
Create Custom Board
-------------------

To create a custom board, after the module has been run from Python's GUI (IDLE),

1) create a variable to hold the board_object.

		Example:
			myBoard = board(9,9)

		This assigns myBoard to have a 9x9 board with all zeroes in each spot.


2) To fill in custom values, a method named: setRowAndCol(x,y,value) is defined in the board class.

	x - Represents which row		  #### ROWS AND COLS ARE ZERO BASED INDICING. 0 is the first row, 8 being the last ####
	y - Represents the column		  #### ROWS AND COLS ARE ZERO BASED INDICING. 0 is the first col, 8 being the last ####


	value - The number the user would like in the spot corresponding to x (row) and y (col).    #### MUST BE A SINGLE DIGIT, 1 - 9 ONLY VALUES SUPPORTED ####

		Example:
			myBoard.setRowAndCol(5,8,2)

		This sets the value at row 5, column 8 to be set to the value 2.  #### REMEMBER ROWS AND COLS ARE ZERO BASED INDICING, 8 IN THIS CASE IS THE LAST COL, NOT 9 ####

3) Run board:
		Example:
			dfs(myBoard)

		The program will then start executing, printing every state, with every decision made.
		When finished, the solution will be the last board shown, the word "DONE" will appear and finally the module will ask if the user wants to close the window.


--------
Comments
--------

Since the implementation is pure brute-force, some boards may take a considerable amount of time to solve. 20+ mins
For example, board1() - takes the solver a significant amount of time to solve.
The remaining boards provided will take just a matter of seconds.




Nalseez Duke
