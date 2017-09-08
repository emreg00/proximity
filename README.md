
# Proximity

Jupyter (IPython) [Notebook](proximity.ipynb) and required files for the proximity-based analysis in the "Network-based *in silico* drug efficacy screening" manuscript.
Known drug-disease associations, proximity and relative efficacy values are given in "proximity.dat" and "palliative.csv" files.

## Required packages

- R kernel for Jupyter
- ROCR (or pROC) 
- ggplot2
- beanplot

## Calculating proximity

See [toolbox](https://github.com/emreg00/toolbox) package for calculating proximity.

For instance, to calculate the proximity from (A, C) to (B, D, E) in a toy network:

```python
>>> from toolbox import wrappers
>>> file_name = "data/toy.sif"
>>> network = wrappers.get_network(file_name, only_lcc = True)
>>> nodes_from = ["A", "C"]
>>> nodes_to = ["B", "D", "E"]
>>> d, z, (mean, sd) = wrappers.calculate_proximity(network, nodes_from, nodes_to, min_bin_size = 2, seed=452456)
>>> print (d, z, (mean, sd))
(1.0, 1.3870748387117167, (0.67100000000000004, 0.2371897974197035))
>>>
```

## Data files

The [data](https://github.com/emreg00/proximity/tree/master/data) folder contains 

- disease/disease_genes.tsv: (MeSH term, gene ids) Disease-gene associations for MeSH disease terms curated in Menche et al. (2015, Science)
- target/drug_to_geneids.pcl.all: (DrugBank id, gene ids) Drug targets for all the drugs in Drugbank 
- indication/disease_to_drugs.pcl.source: (MeSH term, DrugBank ids) Drug indication information from "source" database (MEDI, Metab2MeSH, KEGG or NDFRT)
- network/network.sif: (Geneid 1 Geneid) Human interactome curated in Menche et al. 
- toy.sif: toy network used in the example

Note that the analysis in the paper (whose citation below), uses a subset of the drugs and diseases given in these files, see Methods in the paper for details.

# Citation

Guney E, Menche J, Vidal M, Barab&aacute;si AL. Network-based in silico drug efficacy screening. Nat. Commun. 7:10331 doi: 10.1038/ncomms10331 (2016). [link](http://www.nature.com/ncomms/2016/160201/ncomms10331/full/ncomms10331.html)

