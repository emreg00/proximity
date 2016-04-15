
# Proximity

Jupyter (IPython) [Notebook](proximity.ipynb) and required files for the proximity-based analysis in the "Network-based *in silico* drug efficacy screening" manuscript.
Known drug-disease associations, proximity and relative efficacy values are given in "proximity.dat" and "palliative.csv" files.

# Citation

Guney, E. et al. Network-based in silico drug efficacy screening. Nat. Commun. 7:10331 doi: 10.1038/ncomms10331 (2016). [link](http://www.nature.com/ncomms/2016/160201/ncomms10331/full/ncomms10331.html)

## Required packages

- R kernel for Jupyter
- ROCR (or pROC) 
- ggplot2
- beanplot

## Calculating proximity

See [toolbox](http://github.com/emreg00/toolbox) package for calculating proximity.

For instance, to calculate the proximity from (A, C) to (B, D, E) in a toy network:

```python
>>> from toolbox import wrappers
>>> file_name = "toy.sif"
>>> network = wrappers.get_network(file_name, only_lcc = True)
>>> nodes_from = ["A", "C"]
>>> nodes_to = ["B", "D", "E"]
>>> d, z, (mean, sd) = wrappers.calculate_proximity(network, nodes_from, nodes_to, min_bin_size = 2)
>>> print (d, z, (mean, sd))
(1.0, 0.97823676194805476, (0.75549999999999995, 0.24993949267772786))
>>>
```

