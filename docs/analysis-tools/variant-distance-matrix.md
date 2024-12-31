**Variant Distance Matrix**
===============
About the Variant Distance Matrix Tool
--------------------------
The Variant Distance Matrix tool calculates the disimilarity between variant sets in the database and stores the results back into the database. It only calculates the distances between variant sets of the same species and includes sanity checks to ensure that duplicate or improper calculations do not occur. This allows for other tools, most notably the SimilarVariantSet tool, to quickly determine relationships between variant sets. 

The Variant Distance Matrix tool makes one assumption when calculating the distance between variant sets: the genome is static within the same species. In other words, the variant distance matrix tool assumes that any two variant sets for which the distance is calculated have the same reference genome. This allows the tool to assume that the distance between two variant sets is only a function of the differences between the variants in the variant sets and not any other outside variables. Since both variant sets have the same static genome, the distance is calculated using the following formula:

![variant distance equation](images/variant_distance_equation.png)

Using the Variant Distance Matrix Tool
--------------------------
This tool mainly functions as a helper tool to the VariantBatchUpload and SimilarVariantSet tools and is unable to be called from the website. Upon the upload of a VariantSet, multiple Variant Distance Matrix instances are forked off to calculate the distances between the new VariantSet and all existing variant sets in the database. The SimilarVariantSet uses this tool when any two uploaded variant sets do not already have an existing distance in the database. The SimilarVariantSet then forks off instances of the Variant Distance Matrix tool in order to calculate these distances.

Both tools pass in two parameters to the Variant Distance Matrix tool: new_gsid and gs_ids. The new_gsid contains the new genset id for which the distances between all of the geneset ids in the gs_ids parameter must be calculated for.

The results of the tool run are inaccessible for users through the website.

Options
-------
There is one option that can be used in conjunction with this tool.

### Disable Sanity Check
 The Disable Sanity Check option can be set to True in order to speed up distance matrix creation. This option disables the two sanity checks that are present in the tool and does the following checks.

  * the genesets are of the same species
  * the distance hasn't already been calculated
  * the geneset is a variantset
  If it is assured that the genesets passed in fulfill these criteria, the sanity checks can be turned off in order to speed up the creation of the distance matrix.

### API Tool

To run the VariantDistanceMatrix tool, use the following API url.
`https://www.geneweaver.org/api/tool/VariantDistanceMatrix/<apikey>/<gs_id>/<gs_ids>/<sanity_check>/`

The parameters are as follows:

* apikey - your geneweaver apikey 
* gs_id - the gs_id of one of your variant sets that you wish to calculate a distance matrix for 
* gs_ids - the remaining gs_ids of your variant sets that you wish to calculate a distance matrix for
