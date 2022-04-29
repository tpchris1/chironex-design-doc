# Design Details
*Design details and implementation of Chironex*
 
## class Message
* Messages are left behind in each cell by Jellyfish
```
    int capacity;
    int messages[]; // heapq with (score,weight) as element
    
    void update(score, weight); 
    void get();
```

}

class Cell{
```
    int X 
    int y 
    Message msg = Message(msg_capacity)
    
    void update_msg(score, weight)
    void get_msg()
    void get_data()
    
```    
}

class Grid{
```
    tuple shape # (4,3) row 4 col 3 
    dict() grid 
    int msg_capacity 
    int n_features 
    int n_classes 
    
    void read(data)
    void get(coord)
```
}

class Learner {
* Machine Learner for each Jellyfish 
 
``` 
    int hidden_nodes
    int batch_size
    int n_iter
    int verbose
    int random_state
    int lr
    
    void forward(x);
    void fit(X, y);
    void predict(X);
    void score(X, y);
    void weight();
    void set_weight(weight);
    
```
}


class Jellyfish {
```
    int n_features
    int n_classes
    Learner learner = TorchMLP(n_features, n_classes) // machine learner
    
    void interact(cell)
    void leave_trace(X, y)
    void score(X, y);
    void predict(X);
    
    void merge(weight1, weight2, mode)
```

}

class logger{
```
    idx
    jellyfish
    scores
```
}

class Metadata{
```
    entity
    coord
```
}


class Engine {
```
    int grid_width 
    int grid_height 
    int max_iter 
    int n_jellyfish
    int msg_cap 
    int time # iteration counter

    train_data, test_data
    X_test = test_data[:, :-1]
    y_test = test_data[:, -1]
    swarm = [] # array of jellyfish and their coordinates
    ocean = Grid((self.grid_height, self.grid_width), self.msg_cap)
    ocean.read(train_data)
    int n_features 
    int n_classes 


    swarm = [
        Metadata(Jellyfish(self.n_features, self.n_classes), \
                gen_random_coord(self.grid_height, self.grid_width)) \


    logger = [Logger(i, val.entity) for i, val in enumerate(self.swarm)]
    eval_when = []
    eval_mean = []
    eval_std = []
    agreement = [] # annotator's agreementＹ
    
    void run()
    void _run_one_step()
    void _validate()
    void _transition()
    void plot_individual_result()
    void plot_swarm_result()
    
```
}



