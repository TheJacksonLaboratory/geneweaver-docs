## Variant Pipeline

5 api endpoints are created for the following 5 pipelines: eggo, eggv, eggr, eggix, and eggin. Each pipeline has a get endpoint to retrieve the information from running each entire pipeline. 
 
The pipeline can be found on Swagger UI through running Geneweaver on Watson and use this link: http://localhost:8889/api/

Each api will load a default configuration file in yaml format. The suggested configuration information is the following:

**environment:**

    - hpc: true 
    - local: false  
    - custom: false   
	- cores: 4    
    - processes: 4    
    - jobs: 15
    - memory: '40GB'
    - walltime: '05:00:00'  
	- interface: 'ib0'  

**directories:**

    - data: 'data/'  
	- temp: ~  

**scheduler:** ~

**workers:** ~

**overwrite:** true  

**species:** ~  

**format:** tsv  

**orthology:**

  - species1: hg38  
  - species2: mm10  

And the following is the requirement for Eggv:

The EGG:V pipeline has some hefty storage and memory requirements.  
**Storage:**  
To be safe, at least **500GB** of disk space should be available if both **hg38** and **mm10** builds will be processed.  
**Memory:**  
The lowest amount of total available memory this pipeline has been tested with is **450GB**.  
Since processing is done in-memory, all at once, systems with total memory below **400GB** might not be able to run the complete pipeline.  
**CPU:**  
Use as many CPU cores as you possibly can.
