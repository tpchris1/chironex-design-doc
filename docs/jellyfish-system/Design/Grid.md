# Grid class
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
