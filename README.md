# DGEval
## Setting up the environment
We have set up our environment using conda and have provided a conda environment yaml file. 
In order to replicate our environment please download conda from [here](https://conda.io/projects/conda/en/latest/user-guide/install/linux.html) and run 
```
conda env create -f environment.yml
```

## Evaluating the models
We have provided a python file for each model/dataset combination we did in order to run any of the evaluations please run 
```
python <model>-<dataset>.py
```
For example for the TGN model with the wikipedia dataset you can run 
```
python tgn-wikipedia.py
```
## References
