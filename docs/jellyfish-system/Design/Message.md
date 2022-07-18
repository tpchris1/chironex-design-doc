# Message class
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
