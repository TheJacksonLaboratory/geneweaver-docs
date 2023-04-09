
GeneWeaver utilizes several external data sources to provide users with a rich set of 
genomic features and gene associations. 

These data sources include:

- [Ensembl](http://www.ensembl.org/index.html)
- [Entrez](https://www.ncbi.nlm.nih.gov/Web/Search/entrezfs.html)
- [UniGene](https://ncbiinsights.ncbi.nlm.nih.gov/tag/unigene/)
- [MGI](https://www.informatics.jax.org/)
- [HGNC](https://www.genenames.org/)
- [RGD](https://rgd.mcw.edu/)
- [ZFIN](https://zfin.org/)
- [FlyBase](https://flybase.org/)
- [Wormbase](https://wormbase.org/)
- [SGD](https://www.yeastgenome.org/)
- [miRBase](http://www.mirbase.org/)
- [CGNC](https://bmcgenomics.biomedcentral.com/articles/10.1186/1471-2164-10-S2-S5)


## Background
Why bother with all these external data sources? Why not just use one?

In genomics research, there are different types of gene and microarray identifiers 
because the same gene can be referred to by different names or IDs, depending on the 
context or the source of the information. This can happen even for genomic features 
within the same species! All these different identifiers can create confusion and make 
it difficult to compare and integrate data from different sources.

Why are there so many different identifiers, you ask? There are a multitude of reasons,
some of which are historical, some of which are technical, and some of which inherent to
biology. 

A given gene may have multiple names or IDs that have been used in different 
contexts as a result of how naming and annotation has evolved over time. It also can be
the case that different databases just used different conventions. Annotations and
naming conventions are also updated as new information about the function and structure 
of genes becomes available.

Genotype platforms, the methods or tool used to identify and detect genetic variations,
can differ in their design and layout, which can affect the way genes are represented.
This can lead to different probe IDs or other identifiers being used to refer to the 
same genomic features on different platforms.

Genomic feature identifiers can also differ between different species, since different 
organisms have different sets of genes and thus different naming conventions for those 
genes. Even if the same identifier is used across species, it may not refer to the
same genomic feature, and the genomic feature itself might have entirely different 
function. 

## GeneWeaver's Solution
GeneWeaver solves this problem by integrating data from multiple sources (listed above)
and mapping all the different identifiers to a single, unified set of internal 
identifiers.

This allows researchers to upload data from different sources to the same platform, and
allows tools to operate of data from different sources without having to worry about
the differences in the identifiers used by those sources.

Geneweaver also uses homology information to map paralogs and orthologs (collectively
knows as homologs) across and within species. This allows researchers to perform 
cross-species analysis, and to identify conserved and divergent biological functions.

This concept is explained in more detail in the 
[Geneweaver Data Model](./geneweaver-data-model.md) concepts page, and in the
[Data model](/reference/data-model) reference page.
