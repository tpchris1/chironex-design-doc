# Design
*Design details and implementation of Chironex*



class Message{
    /* Messages are left behind in each cell by Jellyfish */
    int capacity = 0;
    int messages[]; // heapq with (score,weight) as element
}

class Cell{
    int data[][]; // batch of data
    Message messages[]; // outputs for several jellyfish (variable sized array)
    
    void append(int []); // append new message to messages
    int [] yield(int []); // give (data, msg) of given coordinate
}

class Grid{
    Cell cell[][];
}

class DNN {
    double weights[];
    double bias[];
    
    void back_propagate(int [], int[]);
}

class Learner {
    /* Machine Learner for each Jellyfish */
    DNN network;
    
    void fit(int [], int[]);
    void predict(int []);
}

// void Converter() {
//     /* Convert variable size input to fixed one*/
// }

class Jellyfish {
    Learner leaner; // machine learner
    Converter converter; // convert jellyfish messages to fixed size
}

struct Coordinate{
    int x, y; // coordinate
}

class Engine {
    int max_iter;
    int time; // time counter for each iteration
    Jellyfish& swarm; // swarm of jellyfish
    Coordinate coord[]; // all coordinate of jellyfish
    Cell[] data; // 
    
    
    void transition(void); // define how coordinate changes
    void train(void); // train all jellyfish
    
    void train(void) {
        for (auto jellyfish : swarm) {
            auto coord = coord(jellyfish);
            auto batch = data.yield(coord);
            Message msg = jellyfish.fit(batch);
            todo.push((msg, coord));
        }
        
        while (!todo.empty()) {
            msg, coord = todo.top();
            todo.pop();
            date[coord].append(msg);
        }
    }
}

class Jellyfish:
    def __init__(self):
        self.converter = Converter(o_dim=1)
        self.learner = MLPClassifier()
        self.merge_functions = {"avg": merge_avg} 

def merge(self, mode="avg", w1, w2):
    return self.merge_functions[mode](w1,w2)

def merge_avg(w1,w2):
    result_weight = []
    for m1, m2 in zip(w1[0],w2[0]):
        result_weight.append((m1+m2)/2)
    result_bias = []
    for m1, m2 in zip(w1[1],w2[1]):
        result_bias.append((m1+m2)/2)
    
    return (result_weight, result_bias)

def interact(self,cell,):
    X,y = cell.get_data()
    msg = cell.get_msg()

    if msg:

    else:
        self.learner.fit(X,y)

