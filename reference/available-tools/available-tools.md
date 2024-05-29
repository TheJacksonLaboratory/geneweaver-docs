
!!! warning "Work in progress"
    [//]: # (TODO)
    Geneweaver is in the process of repackaging its tools. This documentation is
    here for reference, based on existing and legacy tool packaging, and will be updated
    as each tool is repackaged.

    Complete documentation on the legacy versions of analysis tools can be found in the
    [legacy documentation](https://geneweaver.org/help/#analysis-tools).

### HiSim Graph
The HiSim Graph, short for Hierarchical Similarity Graph, is a tool for grouping 
functional genomic datasets based on the genes they contain. For example: The user may 
want to determine what a set of experiments on alcohol preference have in common, and 
what makes various experiments unique from one another. Alternatively, one may wish to 
take a large set of studies of related phenomena and identify their shared or distinct 
substrates. In this situation one may want to know whether there is a shared biological 
basis for addiction and learning, and if so, what the substrate is. The user might also 
want to examine studies of a large number of related disorders and determine whether a 
more appropriate biologically-based classification can be constructed.

The HiSim Graph Tool is designed to address these goals; it presents a tree of 
hierarchical relationships for a set of input GeneSets. The structure is determined 
solely from the gene overlaps of every combination of GeneSets.

### GeneSet Graph
The GeneSet Graph is designed for the user in need of a partitioned display to 
illustrate just how tied genes are to one another. For example: a user in need of a 
GeneSet Graph would look for visual references more than chemical references or 
references by utility. A GeneSet Graph can also help pick apart the most valuable or 
most occurring genes depending on the user’s preference.

### Jaccard Similarity
The Jaccard Similarity Tool displays a matrix of Venn diagrams, which can be very useful
for quickly finding overlapping GeneSets and evaluating the similarity of results across
a collection of experiments. This snapshot may enable you to determine which can be 
removed or kept for more complex comparison analysis (such as the HiSim Graph).

### GeneSet Clustering
Clustering is one of the most powerful tools in bioinformatics, where classifications 
are too strict for data distinction, clustering helps give the user an evaluation that 
is not so distinct.

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
The Boolean Algebra Tool performs basic set operations on at least two Gene Sets. 
Results are displayed as lists of genes beloging to one of the three different types of 
set operations: Union, Intersect, and Symmetric Difference. Furthermore, results allow 
users to quickly determine new relationships between Gene Sets and create a new Gene Set
based on set-derived findings.

### DBSCAN Gene Clustering
DBSCAN (Density-Based Spatial Clustering of Application with Noise) is a clustering 
algorithm that groups genes into clusters based on how closely related the genes are.

#### Why Use the DBSCAN Tool?
In general, clustering is used to find patterns or outliers within data sets. In this 
implementation of DBSCAN, genes in the same cluster would be considered similar, while 
genes in different clusters would be less similar. An explanation of DBSCAN can be found
[here](https://en.wikipedia.org/wiki/DBSCAN). Within Geneweaver, this tool can be used 
to infer relationships between genes. For example, if clusters with similar genes 
continue to appear in tests across multiple data sets, one could say that these genes 
are closely related.
