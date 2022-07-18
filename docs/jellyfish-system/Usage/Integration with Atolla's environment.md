# Usage

## Introduction
- Trained Jellyfish act as critter brains in Atolla's environment
- Users need to embed Jellyfish into Atolla's environment
- And then train and export weights of Jellyfish as a result to be applied to the environment

---

## Dataset
2. When integrate with Atolla, the number of class should match the number of action in Atolla's settings
3. Current setting of Atolla requires number of class >= 4
4. A sample dataset `glass.csv` matches the requirement is provided in the repo 

!!! warning
    Atolla had not implemented the interface to use Chironex as critter by 05/2022

---

## How to use
1. Preprocess dataset
2. Copy dataset to `Critter_Env_Interface` folder
3. Modify `core.py` to of `read_csv` to make sure the dataset can be read
4. Use `python core.py` to generate weights
5. Use function `load_info` in `core.py` to load the weights into Atolla's environment 