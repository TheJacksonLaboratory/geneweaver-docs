# Foundational Concepts
This section provides a quick introduction to some key concepts that underpin the entire
Geneweaver ecosystem. This section should be enough to get you started, but for a 
comprehensive definition, please see the [Concepts](../concepts/index.md) section.

## Genes (Genomic Features)
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

## GeneSets
The central entity in GeneWeaver is called a "GeneSet". A GeneSet  is a collection of 
genomic features that are related by a common biological function, pathway, process, or other
biological concept. GeneSets are used to organize and analyze heterogeneous functional
genomics data.

Genesets are a fundamental component of Geneweaver, as the system uses them to perform 
integrative analysis of functional genomics data. Researchers can compare and combine 
multiple genesets to identify overlaps or similarities, which can provide insights into 
the biological processes and pathways that are involved in the data being analyzed.

## Species
Currently, 10 species are supported:

- Mus musculus - The Mouse 🐁
- Homo sapiens - The Human 🧍
- Rattus norvegicus - The Rat 🐀
- Danio rerio - The Zebrafish 🐟
- Drosophilia melanogaster - The Fruit Fly 🪰
- Macaca mulatta - Rhesus Monkey 🐒 
- Caenorhabditis elegans - The Roundworm 🪱
- Saccharomyces cervisiae - Brewer's Yeast 🍺
- Gallus gallus - The Chicken 🐓
- Canis familiaris - The Dog 🐕