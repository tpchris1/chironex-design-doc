# Training and Plotting


## Introduction
- Simply train and test with dataset
- Plot the performance of Jellyfish

---

## Dataset
1. In training mode, the number of class does not matter
2. Any tabular classification dataset can be used to train Chironex after preprocessing 
3. A sample dataset is provided in the repo which is the cleaned and preprocessed version of `Titanic` dataset
4. This dataset contains only features without the first line of the names of all features
5. All other datasets should be preproccessed into the same format like the sample dataset to proceed with Chironex

---

## How to use
1. Preproccess dataset
2. Copy dataset to `jellyfish-system` folder
3. Open `engine.py` -> Jump to `if __name__ == __main__:`
4. Change filename in read_csv to your own dataset
5. Since this is only training, use `python engine.py` to execute
6. Several plots would be visualized regarding the result of individual and swarm result