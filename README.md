# MinesweeperDQL
Created a minesweeper solver that uses a Deep Q learning approach.

# Grid Environment :
The approach solves for the smallest grid world environment of minesweeper: 9x9 grid with 10 mines. This environment was implemented using a class implementation in python. This grid world environment has 81 states where each state can be represented as a matrix. The number tiles are represented using a number from 0 – 8, where the number represents the number of mines neighboring the tile, and the numbers 9 is used to represent a mine and 10 is used to represent an uncovered tile. The actions can be to “click” any of the tiles.

# Neural Network :
4 layers including the input and output layer are used to build the neural network. The input layer accepts the current state of the board in the form of a vector where each entry is a state corresponding to a tile (For example, if tile (0,3) has a mine, the 4th element in the vector would have the value 9). The input layer is the size of the board, for a 9x9 board the input dimension would be 81 x 1. The output layer gives the q values where the action is represented by the index (For example, if the ith index has the greatest Q value in our output, the associated action would be to click the corresponding tile on the board that the ith index maps too). The 2 hidden layers have input dimensions 120 x 1 and 100 x 1 respectively.

# Reward Structure:
The reward structure in my approach is designed to guide the agent to clearing the Minesweeper level and its set as follows:
For a win, when all the tiles are uncovered without stepping on a mine and all the mines are flagged, the reward is set to +1.
For a loss, where the agent steps on a mine, the reward is set to -1.
For a positive progress, where a new tile is uncovered but doesn’t lead to a win or a loss, the reward is set to 0.5.
For a no progress, where a previously discovered tile is discovered again, the reward is set to -0.5.
