# DGEval
## TGN (We should run this first because it downloads the datasets)
We draw heavy inspiration from the examples provided from the pytorch-geometrics library and we run it at our own convenience 
We run each dataset 5 times and calculate the mean average precision and mean ROC AUC and their standard deviations
### Setting up the environment
We have set up our environment using conda and have provided a conda environment yaml file. 
In order to replicate our environment please download conda from [here](https://conda.io/projects/conda/en/latest/user-guide/install/linux.html) and run 
```
cd TGN
conda env create -f environment.yml
```
### Evaluating the models
We have provided a python file for each dataset we did. in order to run any of the evaluations please run 
```
python tgn>-<dataset>.py
```
For example for the TGN model with the wikipedia dataset you can run 
```
python tgn-wikipedia.py
```

## TGAT 
We rerun the implementation provided by the author. To rerun that example clone the repository of the author linked below.
After running the TGN model you will find a directory called data with both the wikipedia and reddit dataset. In each direction there's a raw directory with a csv file in it. Just copy it to the processed dir in the TGAT repo and reproduce. 
To re run also perform the following in the root directory of this repo
```
git clone git@github.com:StatsDLMathsRecomSys/Inductive-representation-learning-on-temporal-graphs.git
cd Inductive-representation-learning-on-temporal-graphs
cp ../data/JODIE/<dataset-name>/raw/<dataset-name>.csv
# You have to uncomment the repo of your interest in the process.py file
python process.py 
python -u learn_edge.py -d wikipedia --bs 200 --uniform  --n_degree 20 --agg_method attn --attn_mode prod --gpu 0 --n_head 2 --prefix hello_world
```

## Heuristic 
For running the heuristic we leverage the implementation offered here https://github.com/xkcd1838/bench-DGNN/tree/master
We provide the config file for running our datasets with the heuristics we are concerned with.
```
# We start by cloning the repo
git clone git@github.com:xkcd1838/bench-DGNN.git
# We provide a config file for each heuristic and dataset combo to run the model with one of our config files
cd bench-DGNN/experiment/
python run_exp.py --config_file ../../DGEval/bench-config/j-wiki.yml
```

## References
1. https://github.com/pyg-team/pytorch_geometric/blob/master/examples/tgn.py
2. https://github.com/StatsDLMathsRecomSys/Inductive-representation-learning-on-temporal-graphs/blob/master/README.md
3. https://github.com/xkcd1838/bench-DGNN/tree/299fee7dda057c6e9479bcb713afbc1a7c31b16b
