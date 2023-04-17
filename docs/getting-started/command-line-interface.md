# Command Line Interface

Geneweaver provides a command line interface for interacting with the GeneWeaver web 
application. The command line interface is a python package called 
[`geneweaver-client`](https://pypi.org/project/geneweaver-client/), available on 
[PyPI](https://pypi.org/project/geneweaver-client/).
Users should consider using the command line interface if they want to run the analysis
tools locally, if they want to automate the uploading or downloading of data to/from 
the web application, 

## Installation

### Requirements
The `geneweaver-client` package requires python 3.7 or greater.

### From PyPI
To install the `geneweaver-client` package from PyPI, run the following command:

```console
$ pip install geneweaver-client
```

### From Source
To install the `geneweaver-client` package from source, run the following commands:

!!! note 
    You will need to have [poetry](https://python-poetry.org/) installed.

```bash
git clone git@github.com:bergsalex/geneweaver-client.git
cd geneweaver-client
poetry install
```

## Usage

!!! warning "Coming Soon"
    [//]: # (TODO)
    For now, please use the built-in help to learn about the command line interface.
    ```
    $ geneweaver --help    
    ```