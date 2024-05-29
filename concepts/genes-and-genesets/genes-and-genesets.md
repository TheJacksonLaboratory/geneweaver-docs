
## Genomic Features (Genes)
A genomic feature 🧬 is any region of DNA that has a specific function or role in the 
genome. Some common genomic features include genes, exons, introns, promoters, and 
enhancers. Genomic features can be identified by a variety of methods, including 
sequencing, hybridization, and annotation.

In GeneWeaver, a genomic feature is a unique identifier for a genomic feature in a
particular organism, mapped from an external data source. Genomic features are the basic
unit of analysis, and are used the building blocks of GeneSets. 

Genomic features are important because they provide a framework for understanding the 
structure and function of the genome. 

## GeneSets
GeneSets 🧬+📂 are the fundamental unit of analysis in GeneWeaver.

A GeneSet contains a list of genomic features, free text descriptive content, ontology 
annotations and gene association scores. In GeneWeaver, Genomic features are mapped 
within and across multiple species. 

a researcher might use Geneweaver to analyze gene expression data from a set of cancer 
patients. By comparing the expression profiles of genesets associated with cancer 
pathways such as the p53 signaling pathway or the cell cycle pathway, the researcher 
might be able to identify genes or pathways that are dysregulated in the cancer samples.

### Geneset Tiers
Genesets are organized into a hierarchy of tiers 🥇🥈🥉🌱🔒, which are used to provide an easily 
recognizable and intuitive way for users to understand the quality and reliability of
the data in a geneset.

| Geneset Tier                                            | Description                                                                                                                           |
|---------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| 🥇**Tier I**<br/>Public Resource Data                   | Professionally curated into another major database and are imported into GeneWeaver,which ensures consistency of metadata.            |
| 🥈**Tier II**<br/>Machine-Generated from public sources | Computationally generated from data in public sources.                                                                                |
| 🥉**Tier III**<br/>Human-Curated Data                   | Directly entered or reviewed by a professional curator for redundancy with existing records and adherence to documentation standards. |
| 🌱**Tier IV**<br/>Submitted to Public-Provisional       | User submitted data that has been shared to the public prior to review.                                                               |
| 🔒**Tier V**<br/>Private User and Group Data, Uncurated | Private data that is considered _confidential_ and **is not** reviewed by a professional curator.                                     |

!!! tip
    For reference level description of Genset Tiers, see the
    [Geneset Tiers](/reference/geneset-tiers) reference page.