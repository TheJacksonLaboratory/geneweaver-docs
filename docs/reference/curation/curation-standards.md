# **Curation Standards Documentation**

Secondary functional genomics data consists of the results of analyzed
experiments in functional genomics. In contrast to primary data stores
such as Gene Expression Omnibus (GEO) in which raw experimental data are
stored, a secondary data store attempts to collect the results of
experimental design and decision-making process of the researcher so
that one may interpret and integrate the gene set centered outcomes of
the studies. Controlling the quality and validity of the large-scale
analysis of secondary data requires the enforcement of interpretable
standards for gene set construction and description. GeneWeaver’s use of
discrete analysis eliminates many barriers to the integration of
heterogeneous data sets across species and experiments. However, it is
important for users to be able to rapidly interpret the nature of gene
sets retrieved from the site, requiring a minimal standard for metadata
associated with secondary data. For this purpose, both unstructured
textual descriptions of the data and structured ontology annotations to
the terms in these descriptions are used to define gene sets. In the
interest of encouraging submission we are cautious not to be too
prescriptive or burdensome to users, but rather to provide guidelines on
standards used by internal curators to assess data quality and clarity
to enable rapid acceptance of community submissions to the data
repository.

Curation Tiers
--------------

|  Tier Name   | Curator Description                                                                                                                                                                                                                                                                                                     |
|:------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Tier I**  | **Public Resource Grade**                    Resource GeneWeaver   Large data sets primarily curated by their parent resource. GeneWeaver ensures consistency of metadata (gene annotations to KEGG, MP and GO, curated functional associations in the Neuroinformatics Framework, Comparative Toxicogenomics Database) |
| **Tier II**  | **Machine-Generated from public sources**    GeneWeaver            Gene sets resulting from genome analysis, not otherwise published in total, e.g. gene co-expression to behavior from GeneNetwork.org, QTL positional candidates from MGI. GeneWeaver curators examine data and metadata.                             |
| **Tier III** | **Human-Curated**                            GeneWeaver            Curated user-deposited data and publication supplements in domains of interest.                                                                                                                                                                      |
| **Tier IV**  | **Submitted to Public- Provisional User**                  User-deposited data made available to the public. All Tier IV is examined for promotion to Tier III                                                                                                                                                          |
|  **Tier V**  | **Private User and Group data- Uncurated**   User                  Data sets deposited for private or group-only analysis                                                                                                                                                                                               |


!!! tip
	GeneSet tiers also have a non-curation meaning, which can be referenced on the [GeneSet Tiers](../geneset-tiers.md) page.
