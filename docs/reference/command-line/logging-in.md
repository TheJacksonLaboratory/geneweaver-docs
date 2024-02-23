# Logging In

This page describes how to log in to the GeneWeaver command line application (`gweave`).

## Requirements
You will need to have installed the `gweave` tool. See 
[Command Line Interface](/reference/command-line/#installation) for installation instructions.

## The `auth` Command Group

!!! tip "Still in beta!"
    The auth command group is still in beta! In the following examples we will prepend
    the `beta` command group to all of our examples.

To log in to the command line application, we will be using the `auth` command group.

??? info "Command Groups"
    If you are not familiar with command groups, see the documentation on `gweave`
    [Command Groups](/reference/command-line/#command-groups).

### Fist Steps

If you have never logged in before, the first think you will need to do is use 
the `login` command.

```
gweaver beta auth login
```

This will prompt you to open a link in your web browser. Once you have opened the link,
you will be prompted to log in to the GeneWeaver web application. Once you have logged 
in, navigate back to the command line application to continue using the `gweave` tool.

```
1. On your computer or mobile device navigate to:  https://geneweaver.auth0.com/activate?user_code=SOME-CODE
2. Enter the following code:  SOME-CODE
```

Note that the code may have been entered automatically for you, in which case you can
continue through without entering the code.

### Seeing you Tokens
You should not need to see your tokens, but if you do, you can use the two tokens 
commands:
```
gweaver beta auth print-access-token
gweaver beta auth print-identity-token
```

### Re-authenticating
You should not have to manually reauthenticate, but if you need to, you can use the 
`--reauth` flag.

```
gweaver beta auth login --reauth
```

This will force the `gweave` tool to restart the loginc process from the beginning.
