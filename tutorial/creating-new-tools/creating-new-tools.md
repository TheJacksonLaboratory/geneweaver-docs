
This page describes the process of creating a Geneweaver Analysis Tool that can be 
integrated directly with rest of the Geneweaver ecosystem, including the Geneweaver
web application.

To create a new tools, you will need to write the interface for your tool in Python,
and then write the interface for your tool in JavaScript. The Python interface will
be used to run your tool locally, and the JavaScript interface will be used to run
your tool in the web application.

Your analysis tool does **not** need to be implemented in Python. It can be implemented
in any language that can be run in a Docker container. The only requirements are that 
your tool must have a public interface implemented in Python, described below, and that 
your tool must be available as a Docker image.

## Quick Start
### Python
To create a new tool in Python, you will need to create a new python package. When 
creating a new package, make sure to follow the 
[contributing guide](../../reference/contributing-guide) and the
[development guide](../../reference/development-guide).

Geneweaver tools use namespaced packages to organize tools and provide a plugin-like
interface. The namespace for Geneweaver tools is `geneweaver.tools`. The name of your
tool should be the name of your package, and should be a subpackage of the
`geneweaver.tools` namespace. For example, if your tool is called `MyTool`, then
your package should be named `geneweaver.tools.my_tool`.

??? tip "Namespaced Packages"
    Namespaced packages are a way to organize and structure Python projects that consist
    of multiple subpackages or modules. Namespaced packages are created by using a 
    dotted namespace in the package name. For example, if you want to create a package 
    called "mypackage" that contains subpackages "foo" and "bar", you could create a 
    namespaced package called "mypackage.foo" and "mypackage.bar". 

    For more information, see the [PEP 420](https://www.python.org/dev/peps/pep-0420/) 
    specification.

## Python Interface
To implement the python interface, you will need to implement a concrete class that
inherits from the `geneweaver.tools.framework.AbstractTool` class. 

The `AbstractTool` class is defined in the `geneweaver.tools.framework` module, which
is the core of the `geneweaver-tools` package.

You will need to install the `geneweaver-tools` package in order to use the 
`AbstractTool` class. You can install the `geneweaver-tools` package from PyPI using
the following command:

=== "Poetry"
    ```console
    $ poetry add geneweaver-tools
    ```
=== "Pip"
    ```console
    $ pip install geneweaver-tools
    ```

### Tool Class

The `AbstractTool` class is actually fairly simple, and only requires you to implement
a few methods. Despite it's simplicity, the `AbstractTool` class provides a lot of 
functionality that you can use to make your tool easier to use. Key to this usability is
the framework's utilization of the [`Pydantic`](https://docs.pydantic.dev/) package.

#### Pydantic

 The `Pydantic` package is a python package that allows you to define data models
in python. These data models can be used to validate and serialize data. The
`AbstractTool` class uses the `Pydantic` package to define the input and output data
of your analysis tool. The `Pydantic` package is also used to define the data models
for the `geneweaver` package, which is used to define the data models for the
Geneweaver web application.

#### The Run Method

The `AbstractTool` class requires you to implement a `run` method. This method is
where you will implement the core functionality of your tool. The `run` method will
be called when your tool is run. 

The `run` method takes a single argument `tool_input`, which is an instance of the 
`ToolInput` class. The `ToolInput` class is defined in the `geneweaver.tools.framework`
module, and is a subclass of the `Pydantic` `BaseModel` class. The `ToolInput` class
is used to define the input data model for your tool.

The `run` method must return an instance of the `ToolOutput` class. The `ToolOutput`
class is defined in the `geneweaver.tools.framework` module, and is a subclass of the
`Pydantic` `BaseModel` class. The `ToolOutput` class is used to define the output data
model for your tool.

This means that the abstract method signature for the `run` method is as follows:

```python
@abstractmethod
def run(self: AbstractTool, tool_input: ToolInput) -> ToolOutput:
    """Run the tool."""
```

#### Input and Output Abstract Properties
Your tool class must also implement two abstract properties: `input` and`output`. These 
properties are used to define the input and output data models, and must return the
uninstantiated `ToolInput` and `ToolOutput` classes, respectively.

The abstract method signatures for the `input` and `output` properties are as follows:

```python
@property
@abstractmethod
def input(self: AbstractTool) -> Type[ToolInput]:
    """Input schema for the tool."""

@property
@abstractmethod
def output(self: AbstractTool) -> Type[ToolOutput]:
    """Output schema for the tool.""" 
```

#### Overrideable Properties
Your tool class can also implement a few overrideable properties. These properties
are used to define the metadata for your tool, and are used to display information
about your tool in the Geneweaver web application.

- `tool_name`: The name of your tool. This is used to display the name of your tool
  in the Geneweaver web application. By default, this is set to the name of your
  tool class.
- `static_files_location`: The location of the static files for your tool. This is
  used to load static data like images and CSS files for your tool in the Geneweaver
  web application. By default, this is set to the `static` directory in the same
  directory as your tool class.

##### Tool Workflow Definition

!!! tip "Scientific Workflows"
    A scientific workflow is a series of interconnected tasks or computational steps 
    that are designed to solve a specific problem or address a scientific question. Not
    all analysis tools will need to define a scientific workflow, and for single-step
    tools, this property can be left undefined as it can be inferred by the Geneweaver
    web application. 

    However, complex analysis tools are encouraged to define a scientific workflow.

    Read more about how Geneweaver uses scientific workflows to define analysis tools
    on the [Scientific Workflows](../reference/scientific-workflows.md) reference page.

- `workflow_definition`: The workflow definition for your tool. This is used to
  define the workflow for your tool in the Geneweaver web application. By default,
  this is set to the `workflow.nf` file in the same directory as your tool class.
- `workflow_type`: The workflow type for your tool. This is used to define the
  workflow type for your tool in the Geneweaver web application. By default, this
  is set to `WorkflowType.NEXTFLOW`. 

## JavaScript Interface

!!! warning
    This section is still under construction.