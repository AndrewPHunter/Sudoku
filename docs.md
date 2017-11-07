# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A:
A naked twin occurs in Sudoku when for any peer set which is the same column, row or square that has the box, contains two boxes with the same two numbers. Due to the rules of Sudoku these means that no other box within the same peer set can have those two numbers since the solution for the naked twins box would account for those numbers.  These means upon identifying a naked twin within a peer group, you can eliminate those values from the list of potential values for every other box in the peer set. This effectively minimizes the search area for solutions for the peer set and thus serves as a form of constrain propogation.

In addition, for the process of finding naked twins , we can apply the constraint that the twin pairs have not already been found, eg ['A1','B1'] and ['B1','A1'] are the same and in order to be a naked twin you have to, by definition, only have two possible values. This allows the search area for naked twins themselves to be constrained.

# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?
A:
The diagonal Sudoku problem places the additional constraint that no two boxes along the main diagonals can have the same number along with the standard constraints of no two boxes within the same row, column or square.  We apply constraint propogation to the diagonal Sudoku problem by including the main diagonals into the appropriate box peer sets for each of the solving techniques employed such as naked twins, eliminate and only choice.

### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solution.py` - Fill in the required functions in this file to complete the project.
* `test_solution.py` - You can test your solution by running `python -m unittest`.
* `PySudoku.py` - This is code for visualizing your solution.
* `visualize.py` - This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the `assign_value` function provided in solution.py

### Submission
Before submitting your solution to a reviewer, you are required to submit your project to Udacity's Project Assistant, which will provide some initial feedback.  

The setup is simple.  If you have not installed the client tool already, then you may do so with the command `pip install udacity-pa`.  

To submit your code to the project assistant, run `udacity submit` from within the top-level directory of this project.  You will be prompted for a username and password.  If you login using google or facebook, visit [this link](https://project-assistant.udacity.com/auth_tokens/jwt_login) for alternate login instructions.

This process will create a zipfile in your top-level directory named sudoku-<id>.zip.  This is the file that you should submit to the Udacity reviews system.

