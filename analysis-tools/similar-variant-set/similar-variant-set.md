**Similar Variant Set**
===============
About the Similar Variant Set Tool
--------------------------
The Similar Variant Set tool finds variant sets of the same species that are the most similar to the input variant set. The tool uses the Unweighted Pair Group Method with Arithmetic mean (UPGMA) approach in order to do this. To run UPGMA, a distance matrix is first created from the results of the VariantDistanceMatrix tool that are stored in the database. 

The Similar Variant Set tool assumes that the variant sets being tested reference the same reference genome. This allows for the tool to determine similarity based solely on the information provided in the variant sets since any possible variant not present in the variant set can be assumed to be equal to the reference genome. 


API Tool
--------------------------
The SimilarVariantSet tool can be run via api at the following url. 

`https://www.geneweaver.org/api/tool/similarvariantset/<apikey>/<gs_id>`  

Options
 
* apikey - your geneweaver apikey 
* gs_id - the geneset id of your variant set 


Visualization
--------------------------
![Scheme](images/hierarchy.png)

The result of Similar Variant Set tool is visualized in a hierarchy graph. From computing with UPGMA algorithm, the relations between each variant will be constructed and sent to the visualization pipeline. 
This hierarchy relation is simply visualized by the color: for each connection, the blue end is parent, and the red end is child. The hierarchy could be traced from each variant’s name as well: we use (A,B) to denote the parent of variant A and variant B. Additionally, user could hover on the links or nodes of interest to see a highlighted version on that part.
