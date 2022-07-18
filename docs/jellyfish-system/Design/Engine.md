# Engine class
> - Engine class 
> - The class to integrate all modules and execute the simulation process
> - Instantiate all variables and run them through designated rounds

### Parameter
- `grid_width`: int, width of the Grid
- `grid_height`: int, height of the Grid 
- `max_iter`: int, number of training iterations
- `n_jellyfish`: int, number of jellyfish 
- `msg_cap`: int, number of messages stored in the Message
- `time`: int, iteration counter
- `train_data`: training data
- `test_data`: test data
- `X_test`: test data attribute
- `y_test`: test data label 
- `swarm` : array, array of jellyfish and their coordinates
- `ocean` : Grid
- `n_features`: int, number of features of training data 
- `n_classes`: int, number of classes of training data 
- `eval_every`: int, number of iteration per evaluation 
- `logger`: Logger object, combine logging information to print 
- `eval_when`: int, evaluation rounds 
- `eval_mean`: float, mean of accuracy
- `eval_std`: float, standard deviation of accuracy  
- `agreement` : array, store annotator's agreement

### Class Variable
- `Metadata`: class, Data structure to for the jellyfish entity and its coordinate
#### Class Prameter
- `entity`: Jellyfish object, entity of the Jellyfish object
- `coord`: tuple of int, coordinate of the Jellyfish

### Functions
!!! note
    `_` prefix for functions are subroutine.
#### run
```py
"""
Run the simulation

Parameters
----------
verbose : bool
    Set to true to print more info

Return 
----------
None
""" 
def run(verbose=False)
```

#### _run_one_step
```py
"""
Run one step of simulation, subroutine of function `run`

Parameters
----------
verbose : bool
    Set to true to log out more info

Return
----------
None
"""
def _run_one_step(verbose=False)
```

#### _validate
```py
"""
Validate the swarm by calculating the following metric
    1. Annotator's agreement
    2. Mean of accuracy
    3. Standard deviation of accuracy

Parameters
----------
step : int
    Current round index

Return
----------
None
"""
def _validate(step)
```

#### _transition
```py
"""
Define how coordinate changes, in place update

Parameters
----------

Return
----------
"""
def _transition()
```

#### plot_individual_result
```py
"""
Plot each of individual Jellyfish's validation accuracy

Parameters
----------

Return
----------
"""
def plot_individual_result()
```

#### plot_swarm_result
```py
"""
Plot the swarm's mean and std validation accuracy

Parameters
----------

Return
----------
"""
def plot_swarm_result()
```

### Outside class functions
!!! info
    Functions not defined in the Engine class but are used within Engine class

#### gen_random_coord
```py
"""
Generate a random 2d coordinate

Parameters
----------
x_boundary : int
    Range of x is [0, x_boundary)
y_boundary: int
    Range of y is [0, y_boundary)

Return
----------
(x_coord, y_coord) : tuple
    2d coordinate
"""
def gen_random_coord(x_boundary, y_boundary)
```

#### shuffle_n_partition
```py
"""
Shuffle and divide the dataset into training and validation set

Parameters
----------
dataset : dataframe
    Target dataset
test_size : int or float
    If data type is int, then |validation set| = test_size
    Else if data type is float, then |validation set| = int(|dataset| * test_size)
normalize: bool
    Whether to normalize values for a feature
random_state: int
    Random seed

Return
----------
train, test : tuple
    Training and validation set
"""
def shuffle_n_partition(dataset, test_size, 
    normalize=False, random_state=42):
```