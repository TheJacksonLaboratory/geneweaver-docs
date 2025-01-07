
## Project Dependencies
### Python Version
All packages in the `geneweaver-*` ecosystem depend on Python version 3.9 or higher. 

If you need to manage multiple version of python on your development machine, we 
recommend using [pyenv](https://github.com/pyenv/pyenv) to manage your python versions.

!!! warning "Support for Python 3.7"
    It's possible that some of the packages in the `geneweaver-*` ecosystem will work
    with Python 3.7, but this is not guaranteed, and is not tested.

### Poetry
All packages in the `geneweaver-*` ecosystem use [poetry](https://python-poetry.org/)
to manage dependencies and build packages. 

The [Python Poetry Documentation](https://python-poetry.org/docs/#installation)
maintains a list of installation instructions for all major operating systems.

### PyTest
All packages in the `geneweaver-*` ecosystem use 
[PyTest](https://docs.pytest.org/en/7.2.x/) as their test runner.

## Package Based Architecture
!!! tip "Package Based Architecture"
    The `geneweaver-*` ecosystem is built around the concept of a package based 
    architecture. This means that each package in the ecosystem is designed to be 
    independent of the other packages. This allows for the ecosystem to be extended 
    and modified without breaking the other packages.

    For more information, see the 
    [Package Based Architecture](../../concepts/package-based-architecture) page.