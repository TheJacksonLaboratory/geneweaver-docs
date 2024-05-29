# API Commands

The `gweave` client has a command group for interacting with the Geneweaver API. This
allows you to do many of the tasks you would usually do on the website from the command
line.

This can be useful for automating tasks, or for running analysis tools locally.

## Requirements
You will need to have installed the `gweave` tool. See 
[Command Line Interface](/reference/command-line/#installation) for installation instructions.

You will need to have logged in to the `gweave` tool. See
[Logging In](/reference/command-line/#logging-in) for instructions on how to log in.

## The `api` Command Group

!!! warning "Still in alpha!"
    The `api` command group is still in alpha! In the following examples we will prepend
    the `alpha` command group to all of our examples.

The `api` command group collects all api interaction commands into a single group. There
are several subgroups, each with their own set of commands.

??? info "Command Groups"
    If you are not familiar with command groups, see the documentation on `gweave`
    [Command Groups](/reference/command-line/#command-groups).

### Genesets

The `genesets` command group is for interacting with genesets.

You can see up-to-date documentation on the command group by using the following help
command:
```
gweaver alpha api genesets --help
```

#### Downloading a Geneset

Downloading a geneset can be as simple as specifying the geneset ID (without the `GS`
prefix).

```
gweave -p alpha api genesets get $GS_ID
```

For example, to download geneset `GS1234`, you can use the following command:

```
gweave -p alpha api genesets get 1234 
```

If you want to download the geneset in a specific gene ID type, you can specify the
`--gene-id-type` flag.

```
gweave -p alpha api genesets get 1234 --gene-id-type=Wormbase
```

To save the geneset to a file, you can use the `>` operator.

```
gweave -p alpha api genesets get 1234 --gene-id-type=Wormbase > geneset_123.json
```

#### Pretty Printing
The `-p` flag will format the results in a way that is easier to read.

You can save the results to a file by using the `>` operator.
```
gweave -p alpha api genesets get 1234 --gene-id-type=Wormbase > geneset_123.json
```


#### GeneIdentifier Types

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