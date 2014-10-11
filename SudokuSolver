from copy import deepcopy
import time

#deepcopy needed to make sure parent's state is not modified


# Checks to see if the current number given by "i" is in the column.
# Returns false if it is, true otherwise
def notInCol(i, state, y):
    z = 0
    if(state[z][y] == i):
        return False
    while(state[z][y] != i) and z < 8:
        z = z + 1
        if(state[z][y] == i):
            return False
    return True

# Checks to see if the current number given by "i" is in the row.
# Returns false if it is, true otherwise

def notInRow(i, state, x, y):
    if i not in state[x]:
        return True
    return False

# Checks to see if the current number given by "i" is in the subSquare (3x3).
# Returns false if it is, true otherwise

def notInSquare(i, state, x, y):
    if x < 3 and y < 3:
        for x in range(0,3):
            for y in range(0,3):
                if state[x][y] == i:
                    return False
    if x < 3 and y >=3 and y <=5:
        for x in range(0,3):
            for y in range(3,6):
                if state[x][y] == i:
                    return False
    if x < 3 and y >= 6 and y <= 8:
        for x in range(0,3):
            for y in range(6,9):
                if state[x][y] == i:
                    return False
    if x >=3 and x <= 5 and y < 3:
        for x in range(3,6):
            for y in range(0,3):
                if state[x][y] == i:
                    return False
    if x >=3 and x <=5 and y >= 6 and y <= 8:
        for x in range(3,6):
            for y in range(6,9):
                if state[x][y] == i:
                    return False
    if x >=3 and x <= 5 and y >= 3 and y <= 5:
        for x in range(3,6):
            for y in range(3,6):
                if state[x][y] == i:
                    return False
    if x >=6 and x <= 8 and y < 3:
        for x in range(6,9):
            for y in range(0,3):
                if state[x][y] == i:
                    return False
    if x >=6 and x <= 8 and y >= 3 and y <= 5:
        for x in range(6,9):
            for y in range(3,6):
                if state[x][y] == i:
                    return False
    if x >=6 and x <= 8 and y >= 6 and y <= 8:
        for x in range(6,9):
            for y in range(6,9):
                if state[x][y] == i:
                    return False
    return True
        
    

# This function will take in a board's state and the action to apply to it
# It then applies the action and returns the new state
def result(state, action):
    state[action[0]][action[1]] = action[2]
    return state



# Class that saves the state passed in as the "Parent's state"
# Applies an action to that state using the function 'result'
# Stores the new state as the node's current state
class childnode:
    def __init__(self, state, action):
        copyList = deepcopy(state)
        self.parent = copyList
        self.state = result(copyList, action)
        self.action = action
        print("---------------------------The action on below board is row indice",action[0],", col indice", action[1],", value", action[2])

# This class is only for the very first state of the board.
# This is due to that the state does not have an action applied to it
# nor does it have a parent state
class node:
    def __init__(self, state):
        copyList = deepcopy(state)
        self.state = copyList

# Class used to define a 9x9 board
class board:
    def __init__(self, rows, cols):
        self.rows = rows
        self.cols = cols
        self.initial = [[0 for x in range(rows)] for x in range(cols)]

    # Method used to set a specific spot on the board to a given value
    def setRowAndCol(self, x, y, value):
        self.rows = x
        self.cols = y
        self.initial[x][y] = value

    # Takes in a state, loops through until it finds a spot where values haven't been generated.
    # Adds all the legal moves for the spot to a list and returns that list.
    def actions(self, state):
        validMoves = []
        for x in range(0,9):
            for y in range(0,9):
                if state[x][y] == 0:
                    for i in range(1,10):
                        if notInRow(i,state,x,y) and notInCol(i,state,y) and notInSquare(i,state,x,y) and (x,y,i) not in validMoves:
                            validMoves.append((x,y,i))
                        if i == 9:
                            return validMoves


# Defines a global variable that increments everytime a new child node is made
childNodes = 0
def increment():
    global childNodes
    childNodes += 1

# Takes in a board, initializes a global variable that holds all the explored states.
# Also defines start_time and end_time variables which will hold the time the program starts and ends execution.
def dfs(board):
    global start_time
    start_time = time.time()
    global end_time
    global explored
    explored = []
    
    return recursiveDFS(node(board.initial),board)

# Called by dfs above so recursion can be used below.
def recursiveDFS(node, board):
    print("")
    
    # If our decision tree is completely empty, it subtracts start_time from end_time to get the total running time.
    # Then prompts to exit the program
    # Will hit this is solution
    if board.actions(node.state) == None:
        print("DONE")
        end_time = time.time()
        print("--- %s seconds ---" % (end_time - start_time))
        print("--- %s child nodes generated ---" % childNodes)
        exit(1)

    # Find the next open spot, and choose the first action out of at most 9 moves.
    for action in board.actions(node.state):
        child = childnode(node.state, action)
        increment()
        
        # Used to print the board state for that child
        for s in child.state:
            print(s)
            
        # Uncomment this to see progression of board move by move
        #time.sleep(1)

        # If the current state hasn't been seen before, recurse on it.
        # If not a solution once there's no more children, add it to the explored list.
        if child.state not in explored:
            recursiveDFS(child, board)
            explored.append(child.state)



# ----------------------------------------------------------------------- #
#        --------------- Preset Boards Defined Below ---------------      #
# ----------------------------------------------------------------------- #

# Very difficult board
def board1():
    game1= board(9,9)
    game1.setRowAndCol(0,2,2)
    game1.setRowAndCol(0,5,3)
    game1.setRowAndCol(0,6,7)
    game1.setRowAndCol(1,1,5)
    game1.setRowAndCol(1,3,7)
    game1.setRowAndCol(1,5,9)
    game1.setRowAndCol(1,6,8)
    game1.setRowAndCol(1,7,1)
    game1.setRowAndCol(1,8,2)
    game1.setRowAndCol(3,1,9)
    game1.setRowAndCol(3,2,8)
    game1.setRowAndCol(3,6,4)
    game1.setRowAndCol(3,7,2)
    game1.setRowAndCol(4,0,5)
    game1.setRowAndCol(4,8,8)
    game1.setRowAndCol(5,1,6)
    game1.setRowAndCol(5,6,5)
    game1.setRowAndCol(5,7,7)
    game1.setRowAndCol(7,0,8)
    game1.setRowAndCol(7,1,4)
    game1.setRowAndCol(7,2,7)
    game1.setRowAndCol(7,3,2)
    game1.setRowAndCol(7,5,1)
    game1.setRowAndCol(7,7,6)
    game1.setRowAndCol(8,2,3)
    game1.setRowAndCol(8,3,4)
    game1.setRowAndCol(8,7,9)
    return game1

# Empty board
def board2():
    game2 = board(9,9)
    return game2

# Smaller version of board1
def board3():
    game3 = board(9,9)
    game3.setRowAndCol(0,2,2)
    game3.setRowAndCol(0,5,3)
    game3.setRowAndCol(0,6,7)
    game3.setRowAndCol(1,1,5)
    game3.setRowAndCol(1,3,7)
    game3.setRowAndCol(1,5,9)
    game3.setRowAndCol(1,6,8)
    return game3

# Random board
def board4():
    game4 = board(9,9)
    game4.setRowAndCol(0,2,2)
    game4.setRowAndCol(1,5,3)
    game4.setRowAndCol(0,6,7)
    game4.setRowAndCol(1,1,5)
    game4.setRowAndCol(4,4,5)
    game4.setRowAndCol(4,5,6)
    game4.setRowAndCol(8,3,7)
    game4.setRowAndCol(8,5,9)
    game4.setRowAndCol(8,6,8)
    return game4
