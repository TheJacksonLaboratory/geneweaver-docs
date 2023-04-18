# GeneWaver Documentation
This repository contains the central documentation site for the GeneWeaver project.
Geneweaver is a web-based software tool for the integration of functional genomics data.
The Geneweaver web application is available at [Geneweaver.org](https://geneweaver.org).

The documentation is built using [MkDocs](https://www.mkdocs.org/) and 
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/),
and is hosted on [GitHub Pages](https://pages.github.com/).

You can view the documentation at https://bergsalex.github.io/geneweaver-docs/.

## Getting Started
First, clone this repository to your local machine:
```bash
git clone git@github.com:bergsalex/geneweaver-docs.git
cd geneweaver-docs
```

To view the documentation locally, you will need to have MkDocs installed on your 
machine. If you don't have it already, you can install it using poetry, or with pip:

#### Using Poetry
```bash
poetry install
```

#### Using Pip
```bash
pip install mkdocs
```

Once you have MkDocs installed, you can view the documentation by running the following
command:
```bash
mkdocs serve
```

This will start a local development server at http://localhost:8000/, where you can view
the documentation in your web browser.

## Contributing
If you notice any errors or omissions in the documentation, please feel free to submit a
pull request with your changes. We welcome contributions from the community!