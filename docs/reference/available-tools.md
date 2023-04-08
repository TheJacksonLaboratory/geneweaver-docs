
### HiSim Graph
The HiSim Graph, short for Hierarchical Similarity Graph, is a tool for grouping functional genomic datasets based on the genes they contain. For example: The user may want to determine what a set of experiments on alcohol preference have in common, and what makes various experiments unique from one another. Alternatively, one may wish to take a large set of studies of related phenomena and identify their shared or distinct substrates. In this situation one may want to know whether there is a shared biological basis for addiction and learning, and if so, what the substrate is. The user might also want to examine studies of a large number of related disorders and determine whether a more appropriate biologically-based classification can be constructed.

The HiSim Graph Tool is designed to address these goals; it presents a tree of hierarchical relationships for a set of input GeneSets. The structure is determined solely from the gene overlaps of every combination of GeneSets.

### GeneSet Graph

### Jaccard Similarity

### GeneSet Clustering

### MSET (Modular Single-Set Enrichment Tool)
Modular single-set enrichment tool (MSET): randomization-based test for list over- or 
under-representation

MSET was developed to compare gene lists. 
From four character lists 
```
gene_list1, 
gene_list2, 
background1, 
background2
``` 
it computes a randomization-based p-value describing the likelihood that the intersect 
of `gene_list1` and `gene_list2` is **underexpressed** or **overexpressed** relative to
randomness alone.

MSET is based on work from [Eisinger et al., 2013, “Development of a versatile enrichment analysis tool reveals associations between the maternal brain and mental health disorders, including autism.” BMC Neuroscience.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3840590/)

### ABBA Gene Search
Given a set of interesting genes, do other genes have similar relationships to known 
sets of genes? For example, given a set of genes known to be related to drug abuse, 
what other genes share similar expression patterns in drug abuse gene sets? 

By answering this question, it becomes possible to elucidate under-studied or obfuscated
genes that may play a role in complex phenotypes.

We have developed a new GeneWeaver tool to address this question, which we call 
Anchored Biclique of Biomolecular Associations (ABBA). 
This tool takes advantage of the large number of collected data and cross-species 
integration to find new genes for investigation.

The search begins with a user-provided list of genes of interest, such as highly-studied
genes with known pathways and relationships. The database then finds any gene sets that 
contain at least N of the genes in the provided list. From the resulting list of gene 
sets, ABBA then isolates any genes that occur in at least M GeneSets but not in the 
initial list. These resulting genes share similar gene set overlap with the original 
input set, but may not have been previously considered in relation to the gene set of 
interest.

### Boolean Algebra

### DBSCAN Gene Clustering


### Combine GeneSets