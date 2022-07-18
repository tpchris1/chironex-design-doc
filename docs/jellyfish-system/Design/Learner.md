# Learner class
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
