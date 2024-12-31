
A scientific workflow is a series of interconnected tasks or computational steps 
that are designed to solve a specific problem or address a scientific question. 

[Nextflow](https://www.nextflow.io/) and 
[Cromwell](https://cromwell.readthedocs.io/en/stable/) are examples of programs that 
allow researchers to define, automate, and execute such workflows.

Scientific workflows can be beneficial when an analysis involves multiple steps, is 
complex, needs to be repeated, involves different platforms or environments, or requires
collaboration.

## Workflows in Geneweaver
Geneweaver uses scientific workflows as part of its model for how its analysis
tools are defined and executed. The `geneweaver.tools.framework` module provides a
`AbstractTool` class that, when used, allows Geneweaver to infer the workflow definition
for single step analysis tools. The `AbstractTool` class also provides a mechanism
for defining workflow definitions for more complex analysis tools that require 
multiple steps or complex execution environments that would be difficult for the 
application to infer.

By default, Geneweaver uses the [Nextflow](https://www.nextflow.io/) workflow engine to 
define and execute workflows. Support for 
[Cromwell](https://cromwell.readthedocs.io/en/stable/) is planned for a future release.

??? info "How Does Geneweaer Do This?"
    Geneweaver uses a service that implements the
    [Ga4GH WES](https://ga4gh.github.io/workflow-execution-service-schemas/docs/)
    specification to define and execute workflows.

    The service is responsible for executing the workflow and returning the results to
    Geneweaver.
    
    Geneweaver's WES service is known as "WESly" and is currently in development. If you 
    are interested in contributing to the development of WESly, head over to the
    [WESly GitHub repository](https://github.com/bergsalex/wesly).
    

### Why Use Workflows?
Geneweaver uses scientific workflows as part of its analysis model for many of the 
same reasons scientists use them in their research. Workflows allow Geneweaver
to define and execute complex analysis tools in a way that is easy to understand
and share with others, and which is both reproducible and platform-agnostic.

Utilizing workflows as the baseline for how Geneweaver implements analysis tools also 
allows Geneweaver to utilize the processes that scientists and researchers use when
defining and executing their own workflows. 
