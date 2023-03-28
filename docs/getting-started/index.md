# Getting Started
The pages in the "Getting Started" section are intended to help you quickly get started 
using the system in a way that is most appropriate for your goals. 

For more in-depth information about the concepts presented in this section, please see
the [Concepts](../concepts/index.md) section and the [Reference](../reference/index.md)
section.

## Foundational Ideas
### GeneSets
The central entity in GeneWeaver is called a "GeneSet". A GeneSet  is a collection of 
genomic features that are related by a common biological function, pathway, process, or other
biological concept. GeneSets are used to organize and analyze heterogeneous functional
genomics data.

Genesets are a fundamental component of Geneweaver, as the system uses them to perform 
integrative analysis of functional genomics data. Researchers can compare and combine 
multiple genesets to identify overlaps or similarities, which can provide insights into 
the biological processes and pathways that are involved in the data being analyzed.

### Genes (Genomic Features)
In GeneWeaver, a "Gene" is a unique identifier for a gene in a particular organism. 
Genes are the basic unit of analysis, and are used to build GeneSets. GeneWeaver 
identifies genes using their unique identifiers, which are called "Gene Identifiers".
A gene identifier is a unique name or number assigned to a gene. 

GeneWeaver supports a variety of different Gene Identifiers from different sources,
including Ensemble (Gene, Protein, and Transcript), MGI, HGNC, and Entrez. Internally,
each Gene Identifier is mapped to a unique Gene ID, which is used to identify genes
across all data sources.

For more information about Genes and GeneSets, please see the
[Genes and GeneSets](../concepts/genes-and-genesets.md) page.

## User Specific Entrypoints


### Researchers

Genomics researchers will find the web application to be the most straightforward
way to get started with GeneWeaver. The web application is a fully integrated platform
for the analysis of heterogeneous functional genomics data. Without ever leaving the 
website, it will allow you to:

- Search for genomics data
- Upload and curate genomic data
- Analyze and visualize genomic data


### Educators & Students

Educators and students will find the ecosystem of software packages to be the most
straightforward way to get started with GeneWeaver. The ecosystem of software packages
is a collection of python packages that are used to build the GeneWeaver web application.


### Developers