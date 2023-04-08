This document outlines the baseline contribution guidelines for all packages in the
`geneweaver-*` ecosystem. These guidelines are intended to concretely define what 
processes and practices a developer should follow when contributing to the project for
their contribution to be accepted.

## Tests
GeneWeaver is a community driven project with a variety of contributors. The project
relies on automated tests to allow developers to be confident that their changes do not
break existing functionality. 

All contributed code should be tested. Test code coverage is calculated using the 
`pytest-cov` module. The minimum code coverage threshold varies per module. Code
should be **well tested** through a variety of tests, not just a high code coverage
percentage.

The `geneweaver-testing` module provides baseline automated tests and fixtures, as do
the other `geneweaver-*` modules. The testing tools in these modules can be utilized
to make writing tests for your code as straightforward as possible.

## Code Style
In order to make the code in the `geneweaver-*` ecosystem consistent, and to make it 
as easy as possible to contribute to the codebase, we have adopted a set of code style
standards and auto-formatting tools. 

### Docstrings
All PyTest Tests and PyTest Fixtures should have docstrings. The docstrings should
follow the [Google Style](https://google.github.io/styleguide/pyguide.html#38-comments-and-docstrings)
for docstrings.

### Type Annotations
All PyTest Tests and PyTest Fixtures should have type annotations. MyPy will be used
to check type annotations.

### Code Linting - Ruff and MyPy
All code in the `geneweaver-*` ecosystem is linted using 
[ruff](https://github.com/charliermarsh/ruff) and [mypy](https://mypy-lang.org/).

GeneWeaver strives to use the most comprehensive set of linting rules reasonably 
available, to both ensure that the code is as clean as possible, and to provide
as much feedback as possible to the developer.

??? abstract "Ruleset Configuration for `ruff`:"
    ```toml
    [tool.ruff]
    select = [
    # Pyflakes Ruleset
        "E", 
    # Pycodestyle Ruleset (E - Error, W - Warning)
        "F", "W", 
    # McCabe Complexity
        "C90",
    # pep8-naming
        "N",
    # flake8-builtins
        "A",
    # flake8-bugbear
        "B", 
    # flake8-annotations
        "ANN",
    # flake8-pytest-stlye    
        "PT",
    # pydocstyle
        "D", 
    # Isort
        "I", 
    # eradicate
        "ERA", 
    # pandas-vet
        "PD", 
    # NumPy-specific rules
        "NPY", 
    ]
    ```

    You can find comprehensive documentation on theses rulesets in the
    [ruff documentation](https://beta.ruff.rs/docs/rules/)

### Code Formatting - Black and Ruff
All code in the `geneweaver-*` ecosystem is formatted using 
[black](https://github.com/psf/black) and [isort](https://pycqa.github.io/isort/).

### Development Process
Before submitting a pull request, please run the following commands to check your code:
```bash
ruff check src/geneweaver tests --fix
black src/geneweaver tests
pytest tests
```
