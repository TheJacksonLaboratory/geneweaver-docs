# Downloading a Geneset From the Command Line
This guide will walk you through how to download a geneset from Geneweaver on the 
command line. This can be useful if you want to automate the downloading of genesets
from Geneweaver, or if you want to use the geneset data in a local analysis tool,
or if you want to access Geneweaver data from somewhere without a web browser.

### Step 0: Install the `gweave` Command Line Tool

##### Optional (But Recommended)
Create a virtual environment for the `geneweaver-client` package.
```
python3 -m venv geneweaver-client
source geneweaver-client/bin/activate
```

```
pip install geneweaver-client
```

### Step 1: Login to Geneweaver
```
gweaver beta auth login --reauth
```


### Step 2: Download Geneset Data
```
gweave -p alpha api genesets get 1234 --gene-id-type=Wormbase
```

The `-p` flag will format the results in a way that is easier to read.

#### Pretty Printing
You can save the results to a file by using the `>` operator.
```
gweave -p alpha api genesets get 1234 --gene-id-type=Wormbase > geneset_123.json
```

#### Specifying Gene ID Type
The `--gene-id` flag is optional. If you do not specify a gene ID type, the default 
will be whatever the geneset was originally uploaded as.

You can specify any gene ID type that is available in Geneweaver, specifically any of the
`GeneIdentifier` types available in the geneweaver.core.enum module 
(`geneweaver-core` package).

##### GeneIdentifier Types

!!! warning
    The `GeneIdentifier` types are reproduced here for convenience, but the most 
    up-to-date list can be found in the `geneweaver-core` package by using the
    `geneweaver.core.enum.GeneIdentifier` class.

- "Entrez"
- "Ensemble Gene"
- "Ensemble Protein"
- "Ensemble Transcript"
- "Unigene"
- "Gene Symbol"
- "Unannotated"
- "MGI"
- "HGNC"
- "RGD"
- "ZFIN"
- "FlyBase"
- "Wormbase"
- "SGD"
- "miRBase"
- "CGNC"