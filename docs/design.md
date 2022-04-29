# Design Details
 
## class Message
> - Traces are left behind in each cell by Jellyfish when visiting
> - These traces are stored in this Message class 

### Parameter
- `capacity`: int, max amount of messages  

### Class Variable 
- `messages`: list, queue to store traces 
- `index`: int, initial = 0, 

!!! warning 
    `index` is used to indicate current size of message, but is deprecated, should be removed from code

### Functions
#### update
```py
"""
Update the current messages queue with score and weight in param

Parameters
----------
score : float
    The score of given weight  
weight : pytorch.tensor
    The weight which needed to be put into this message queue
""" 
def update(score, weight)
```
#### get
```py
"""
Get all scores and weights of current message queue
""" 
def get()
```

---

## class Cell
> - Cell is the fundamental unit for Jellyfish to travel around
> - Composed of a batch of sample data and a Message class to store information 

### Parameter
- `X`: numpy array, training data to store in current cell 
- `y`: numpy array, label data to store in current cell
- `msg`: Message class, messages to store trace of Jellyfish 

### Functions
#### update_msg

```py
"""
Wrapper function to update messages in Message class

Parameters
----------
score : float
    The score of given weight  
weight : pytorch.tensor
    The weight which needed to be put into this message queue
""" 
def update_msg(score, weight)
```
#### get_msg
```py
"""
Wrapper function to get all scores and weights of current message queue
""" 
def get_msg()
```
#### get_data
```py
"""
Get training data and labels from current cell
"""  
def get_data()
```    

---

## class Grid
> - "Sea" for Jellyfish to travel in
> - A 2D array of Cell class which Jellyfish would be put on 
### Parameter
- `shape`: tuple of int, shape of the grid e.g. (4,3) -> 4 rows and 3 cols 
- `msg_capacity`: int, max amount of messages to pass into Message class

### Class Variable
- `grid`: dict
  - `key`: tuple of int, coordinate
  - `value`: Cell class
- `n_features`: int, number of features of training data 
- `n_classes`: int, number of classes of training data 

### Functions
#### read
```py
"""
Generate Grid and sample data into each Cell

Parameters
----------
data : numpy array
    training data to be put onto Grid  
""" 
def read(data)
```
#### get
```py
"""
Get training data and labels from current cell

Parameters
----------
coord : tuple of int
    return Cell of given coord  
"""  
def get(coord)
```

---

## class Learner
> - Machine Learner for each Jellyfish
> - Can be modified by users
> - Current implementation as a MLP 
> - An extention of sklearn estimators 

!!! info
    Actually class name is `TorchMLP(BaseEstimator)` inside file `learner.py`

### Parameter
- `n_features`: int, number of features of training data 
- `n_classes`: int, number of classes of training data 
- `hidden_nodes`: int, default=5, number of MLP hidden nodes 
- `batch_size`: int, default=7, batch size for MLP 
- `n_iter`: int, defualt=10, number of iteration for MLP
- `verbose`: int(bool), default=0/False, print out debug info or not
- `random_state`: int, default=42, random seed
- `lr`: int, default=1e-4, learning rate for MLP

### Class Variable 
- `network`: pytorch.nn.Sequential, Pytorch MLP implementation 

### Functions

#### forward
``` py
"""
Implementation of forward of sklearn estimators of current MLP version

Parameters
----------
x : numpy array
    Training data  
""" 
def forward(x)
```    

#### fit
```py 
"""
Implementation of fit of sklearn estimators of current MLP version
Fit the model to the data X.

Parameters
----------
X : numpy array
    Training data 
y : numpy array
    Training label  
""" 
def fit(X, y)
```
#### _fit
```py
"""
Underlying actual fit function to fit the model to the data X.

Parameters
----------
X : numpy array
    Training data 
y : numpy array
    Training label  
rng: Deprecated, Not used anymore 
""" 
def _fit(self, X, y, rng):
```

#### predict
```py 
"""
Implementation of predict of sklearn estimators of current MLP version
Predict using the model with X.

Parameters
----------
X : numpy array
    Training data 
""" 
def predict(X)
```

#### score 
```py 
"""
Implementation of score of sklearn estimators of current MLP version
Get the accuracy of predictions over labels

Parameters
----------
X : numpy array
    Training data 
y : numpy array
    Training label
""" 
def score(X, y)
```

#### weight
```py 
"""
Retrieve weight of current Learner
""" 
def weight()
```

#### set_weight
```py 
"""
Set weight of current learner to param weight

Parameters
----------
weight : pytorch.tensor
    The weight which needed to be put into Learner
""" 
def set_weight(weight)
```

---


## class Jellyfish
> - Abstract class act as Jellyfish
> - Wrapper class for Learner (Learner as critter)
> - Interaction method are implemented here
> - Merge method are implemented here
> - Mutate method are implemented here (For Atolla's environment)

!!! note
    `Merge` and `Mutate` is implemented in the `jellyfish.py` but is not a part of the class. Whether to integrate it with the Jellyfish class is still debatable
### Parameter
- `n_features`: int, number of features of training data 
- `n_classes`: int, number of classes of training data 

### Class Variable
- `mutate_portion`: float, percentage of weights should be mutated when called 
- `learner`: class Learner, machine learner act as critter

### Functions
#### interact
```py
"""
Interact with the cell
Either train using the data or generate new weights and decide which to store

Parameters
----------
cell : class Cell
    The cell which current Jellyfish is in  
""" 
def interact(cell,verbose=False)
```

#### leave_trace
```py
"""
Leave trace in the Message of this Cell with given data

Parameters
----------
X : numpy array
    Training data 
y : numpy array
    Training label  
""" 
def leave_trace(X, y)
```

#### score
```py
"""
Call score function of Learner

Parameters
----------
X : numpy array
    Training data 
y : numpy array
    Training label  
""" 
def score(X, y)
```

#### predict
```py
"""
Call predict function of Learner

Parameters
----------
X : numpy array
    Training data 
y : numpy array
    Training label  
""" 
def predict(X)
```

#### set_weight
```py
"""
Set the param weight to current Jellyfish

Parameters
----------
weight : pytorch.tensor
    The weight which needed to be put in current Jellyfish
""" 
def set_weight(weight)
```

#### mutate_weight
```py
"""
Call outside class mutate function to mutate weight of current Jellyfish
""" 
def mutate_weight()
```

## class Engine
> - Engine class 
> !!! note
    `gen_random_coord` and `shuffle_n_partition` is implemented in the `engine.py` but is not a part of the class. 


### Parameter
- `grid_width`: int, 
- `grid_height`: int, 
- `max_iter`: int,
- `n_jellyfish`: int, 
- `msg_cap`: int, 
- `time`: int, iteration counter
- `train_data`
- `test_data`
- `X_test`
- `y_test`
- `swarm` : array, array of jellyfish and their coordinates
- `ocean` : Grid
- `n_features`
- `n_classes`
- `eval_every`
- `logger`
- `eval_when`
- `eval_mean`
- `eval_std`
- `agreement` : array, store annotator's agreement

### Class Variable
- `Metadata`:  


### Functions
#### run
```py
"""

""" 
def run(verbose=False)
```

#### _run_one_step
```py
"""

""" 
def _run_one_step(verbose=False)
```

#### _validate
```py
"""


Parameters
----------
step : 

""" 
def _validate(step)
```

#### _transition
```py
"""


""" 
def _transition()
```

#### plot_individual_result
```py
"""

""" 
def plot_individual_result()
```

#### plot_swarm_result
```py
"""

""" 
def plot_swarm_result()
```




