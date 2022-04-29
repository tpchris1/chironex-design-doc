# Usage


## Introduction
1. Currently Chironex can be used on any classification problem
2. Divided into 2 parts:
    - Training and Plotting part
    - Integration with Atolla's environment
### Training and Plotting
- Simply train and test with dataset
- Plot the performance of Jellyfish
### Integration with Atolla's environment
- Trained Jellyfish act as critter brain in Atolla's environment
- Train and export weights of Jellyfish

---

## Dataset
### Training and Plotting
1. In training mode, the number of class does not matter
2. Any tabular classification dataset can be used to train Chironex after preprocessing 
3. A sample dataset is provided in the repo which is the cleaned and preprocessed version of `Titanic` dataset
4. This dataset contains only features without the first line of the names of all features
5. All other datasets should be preproccessed into the same format like the sample dataset to proceed with Chironex

### Apply Chironex as critter in Atolla's environment
1. When integrate with Atolla, the number of class should match the number of action in Atolla's settings
2. Current setting of Atolla requires number of class >= 4
3. A sample dataset `glass.csv` matches the requirement is provided in the repo 
!!! warning
    Atolla did not implement the interface to use Chironex as critter

---

## How to use
### Training and Plotting
1. Preproccess dataset
2. Copy dataset to `jellyfish-system` folder
3. Open `engine.py` -> Jump to `if __name__ == __main__:`
4. Change filename in read_csv to your own dataset
5. Since this is only training, use `python engine.py` to execute
6. Several plots would be visualized regarding the result of individual and swarm result


### Apply Chironex as critter in Atolla's environment
1. Preprocess dataset
2. Copy dataset to `Critter_Env_Interface` folder
3. Modify `core.py` to of `read_csv` to make sure the dataset can be read
4. Use `python core.py` to generate weights
5. Use function `load_info` in `core.py` to load the weights into Atolla's environment 