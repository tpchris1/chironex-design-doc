# Jellyfish class
> - Abstract class act as Jellyfish
> - Wrapper class for Learner (Learner as critter)
> - Interaction methods are implemented here
> - Merge methods are implemented here
> - Mutate methods are implemented here (For Atolla's environment)

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