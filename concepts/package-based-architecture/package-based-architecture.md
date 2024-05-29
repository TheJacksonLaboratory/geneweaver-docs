
GeneWeaver utilizes a package based architecture to allow for the development of new
analysis tools and data types without requiring changes to the core GeneWeaver codebase.
The GeneWeaver project is composed of several python packages that are used to build the
GeneWeaver web application. These packages are also available for use in other projects.

This page describes the GeneWeaver package based architecture, and provides an overview
of why this architecture was chosen for the GeneWeaver project.

## Architecture Overview
A  package-based architecture is a software design approach in which the functionality 
of an application is divided into separate modules, or packages, each of which provides 
a specific set of features or services. These packages can be thought of as 
self-contained units of code that can be developed and maintained independently of one 
another, and can be combined and reused to build larger, more complex systems.

In a package-based architecture, each package typically has a well-defined interface or 
API (application programming interface), which defines how other packages can interact 
with it. This interface provides a clear separation of concerns, allowing developers to 
focus on the specific functionality provided by each package, without having to worry 
about the details of how other packages are implemented.

One of the main benefits of a package-based architecture is modularity. By dividing an 
application into separate packages, developers can more easily manage the complexity of 
the code, and can develop and maintain each package independently of the others. This 
can also make it easier to reuse code between projects, since individual packages can 
be easily extracted and reused as needed.

### Motivation for Package Based Architecture
The package based architecture was chosen for the Geneweaver project so that it remains 
flexible, modular, and scalable over time, while also making it easier to manage and 
maintain the complexity of the codebase.

#### Modularity and Flexibility
A package-based architecture provides a modular design that makes it easier to manage 
and maintain the complexity of the codebase. Geneweaver includes a range of complex 
algorithms, processes and data structures, and dividing the application into separate 
packages allows developers to focus on developing and maintaining each package 
independently of the others. This helps ensure that the application remains stable 
and scalable over time.

#### Reusability
A package-based architecture promotes code reuse, which saves time and effort during 
development. In a scientific application like Geneweaver, there is a need to reuse 
certain algorithms, processes and data structures across different parts of the 
application, and a package-based architecture makes this process easy.

#### Collaboration
A package-based architecture makes it easier for developers to work collaboratively 
on the Geneweaver. By dividing the code into separate packages, developers can work 
on different parts of the application independently, without having to worry about 
conflicts or dependencies on other parts of the codebase.

#### Testing
A package-based architecture makes it easier to test the application. By dividing the
application into separate packages, developers can test each package independently of
the others, which makes it easier to write tests, and easier to identify and fix bugs.

!!! tip "Available Packages"
    A complete reference of the available packages can be found in the 
    [Available Packages](/reference/available-packages) section.