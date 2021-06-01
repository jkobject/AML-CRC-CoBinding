# Cobinging Analysis description

## Recap:

- I had to make some new plots and to complete some missing ones. I have some other plot ideas I can propose.
- I stumbled on many issues in trying to make sure that everything was right in enrichment as it is so core to the paper. I had questions of how to read the enrichment/overlap plots: what is enriched in what. I also made some more enrichment within peaks.
- It also was sometime complex and I needed some literature review for some description of plots

## notebooks:
 
in `html_notebooks/` you can find the notebooks in the html format.
- `CoBinding pre-processing and analysis_v3_remove_single_150.html`:
- `CoBinding Enrichment and Correlation on motifs_remove_single_150.html`:
- `CoBinding Enrichment and Correlation_remove_double_150.html`:
- `CoBinding Enrichment and Correlation_removed_double_150.html`:
- `CoBinding Enrichment and Correlation_v3_removed_single_150.html`:
- `CoBinding Motifs and predictions_removed_single_150_old.html`: 

- `150` is the window extension size for merging peaks in the cobinding matrix
- `remove_*` is the min allows number cobinding peaks for one consensus region: (_removed\_single_: kept only consensus with >1 peak,  etc..)

these files cannot be found on the google drive and I prefer to keep them in github. you can find them [here](https://github.com/jkobject/AMLproject/tree/master/html_notebooks). If they don't open directly on github, you can download them and open them on your browser.

In the most recent versions of each of the 3 notebooks, you can find a _documentation for each plot_ together with the plot name & filename. That will be useful when looking at plots directly in the `results/cobinding/plot/` folder, which contain many more versions of these plots (with different parameters).

you can find a _description of the methods_ in [here](https://docs.google.com/document/d/1JnOC2sc_ajOa1UYg8CL5rlM9DU_La2t6SXf4ewM1Qqc/edit#)

## result/ section:

everything is in `Cobinding_ChIP/` (a couple more info in `chromHMM/`, where the results of running it are storred).

`v3` is the current latest version of the pipeline and data.
The `merged` file is refering to the cobinding matrix. `.npy` files are file that I use to store some matrices. If you get interested in those I can share them in csv format with you. Otherwise they can by openened with python (`numpy.load()`).

`additionalpeaks/` is a folder that contains bed files of peaks that were newly found for each replicate by my chip replicate merging tool. This is mainly for QC puposes (looking at IGV etc..). But it is a pretty good one.
`MV411Merged/` is the merged Bed file from my chip replicate merger tool for each protein.

`ROSE/` is the output from calling ROSE onl all our H3K27ac replicates
`QC/` contaains the latest html QC files from mapping and peak calling on all our ChIP using _multiQC_.

## Plot/ section

Many plots on different paameters (given in the filename)
`*_somNets/` folder is where is stored the enrichemnt over the nodes of each CRC members. 

`*_merge_repicate/` folder is where is stored the plot output of my chip repicate merging tool (similarity, correlation, venn overlap, etc..), it contains the _results.txt_ file where the log of the tool is stored (also mainly used for debugging and QC).

`20`|`50`|`200` are additional parameter number (to the 150 window size parameter), that represents the number of clusters of the clustering algorithm (only on plot where clusters are used).

`bool` & `zscore scale` can also be found in some filename and express the fact that the cobinding matrix was not scaled regularly (0 to 1) to compute the clusters, but scaled by binarizing it or by zscoring it.
