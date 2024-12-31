# `gweave` Command Line Interface

The geneweaver-client library comes with a command line interface that exposes common
functionality for Geneweaver.

## Installation
This library is tested on python version `3.9`, `3.10`, and `3.11` on Ubuntu Linux. The 
library should work on any version of python `3.9` or higher on any system that runs
python.

!!! tip "Using a Virtual Environment"
    A virtual environment is a way to isolate the dependencies of a project from the
    dependencies of the system. This is useful for managing multiple projects with
    different dependencies, and for ensuring that the dependencies of a project do not
    conflict with the dependencies of the system.

    To create a virtual environment for the `geneweaver-client` package.
    ```
    python3 -m venv geneweaver-client
    source geneweaver-client/bin/activate
    ```

To install the `geneweaver-client` package from PyPI, run the following command:
```bash
pip install geneweaver-client
```

## Help Documentation

All of the `gweave` commands come with built-in help. To see the help for a specific
command, use the `--help` flag.

```bash
gweave --help
```

## Alpha & Beta Commands
The `gweave` client is how the Geneweaver team ships early access functionality, and
how we test new features. The `alpha` and `beta` commands are how we expose this
functionality to the community.

??? danger "Alpha Commands"

    The `alpha` commands are for early access functionality. They are not guaranteed to
    work, and they are not guaranteed to be stable. They are for testing purposes only.

    They are considered to be experimental, and they may be removed or changed without
    warning.

    Alpha commands do not have the same level of testing requirements as the rest of the 
    CLI, and may break or change in unexpected ways.

    You can always see information about alpha commands, as well as all commands available
    in the `gweave` CLI, by using the `--help` flag.

    ```bash
    gweave alpha --help
    ```

??? warning "Beta Commands"
    The `beta` commands are for functionality that is _intended_ for general release,
    is considered to be stable and safe to use, but which is still undergoing testing. 

    There is also no guarantee that beta commands will be released beyond beta testing.

    Beta commands are subject to future change and/or removal.

    You can always see information about beta commands, as well as all commands available
    in the `gweave` CLI, by using the `--help` flag.

    ```bash
    gweave beta --help
    ```

## Command Groups
The `gweave` CLI is organized into command groups. Each command group is a collection of
related commands. The alpha and beta commands referenced in the previous section are 
actually two examples of these groups. 

Command groups can also have nested command groups. 

```
gweaver <group> <subgroup> <command> <arguments> <options>
```

In the following example, `alpha` is a command group, and `auth` is a nested command 
group, login is a command, and `--reauth` is an option.

```
gweaver alpha auth login --reauth
```