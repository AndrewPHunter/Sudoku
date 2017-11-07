# Sudoku Solver
[AI Nanodegree Project](https://www.udacity.com/ai)

<p>
This project was performed as part of the Udacity nanodegree program. It solves a [diagonal sudoku](http://www.conceptispuzzles.com/?uri=puzzle/sudoku/rules) puzzle using constraint propogation utilizing the naked twin, elimination and only choice strategies.
</p>
<p>
The full Udacity project description can be found in the [docs](./docs.md)
</p>

### Getting Started
* clone the repo
* restore the project environment

```ss
conda env create -f environment.yml
```

-or -

```sh
pip install -r requirements.txt
```

* run the project

```sh
python solution.py
```

## Main algorithms employed
* [Naked Twins](http://www.sudokudragon.com/tutorialnakedtwins.htm)

```py
def naked_twins(values):
    """Eliminate values using the naked twins strategy.
    Args:
        values(dict): a dictionary of the form {'box_name': '123456789', ...}

    Returns:
        the values dictionary with the naked twins eliminated from peers.
    """
    for unit in unitlist: # go through each peer
        naked_twins = []
        for box in unit:
            if len(values[box])==2: #are we a potential twin?
                for potential_twin in unit:
                    if potential_twin != box and values[box] == values[potential_twin]:
                        #new entry only, eg ['A1','B1']  == ['B1', 'A1']
                        if [box, potential_twin] not in naked_twins and [potential_twin, box] not in naked_twins:
                            naked_twins.append([box, potential_twin])
        for twins in naked_twins:
            for box in unit: # for all peers
                for digit in values[twins[0]]:
                    if box not in twins: # if not the twins
                        values = assign_value(values, box, values[box].replace(digit, ''))

    return values
```

* [Only Choice](http://www.sudokudragon.com/tutorialonlychoice.htm)

```py
def only_choice(values):
    for unit in unitlist:
        for digit in '123456789':
            dplaces = [box for box in unit if digit in values[box]]
            if len(dplaces) == 1:
                values = assign_value(values, dplaces[0], digit)
    return values
```
* [Elimination](http://www.conceptispuzzles.com/index.aspx?uri=puzzle/sudoku/techniques)

```py
def eliminate(values):
    solved_values = [box for box in values.keys() if len(values[box]) == 1]
    for box in solved_values:
        digit = values[box]
        for peer in peers[box]:
            values = assign_value(values, peer, values[peer].replace(digit, ''))
    return values
```

###  Project Layout

The entire project is contained in solution.py albeit not the best situation however it was a requirement for the structure of the assignment for the nanodegree program. The sudoku grid that this program solves is contained at the bottom of the file, in "main" and held in a variable named diag_sudoku_grid.  Dots in the string represent the blanks for the puzzle. The main functions are all above this along with helpers that create the grid and associated peer groups.

### Contributing

This repository is used for a nanodegree program that I am participating in so I will not be accepting pull requests.


