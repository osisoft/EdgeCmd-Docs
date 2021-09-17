---
uid: RetrieveEDSConfiguration
---

# Retrieve EDS configuration

Use EdgeCmd utility to retrieve the configuration of EDS.

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter, you need to add it in the command. For example:

```cmd
edgecmd -port 5591 <RestOfTheCommand>
```

## Retrieve Storage component configuration

1. Access EdgeCmd utility through the command line.
2. Run the following command:

    ```cmd
    edgecmd get -cid Storage
    ```

## Retrieve periodic egress endpoints configuration

<!-- MB 9/16: What is this cmd supposed to do? When I fire it off, I get an error message that the resource cannot be retrieved. -->

1. Access EdgeCmd utility through the command line.
2. Run the following command:

    ```cmd
    edgecmd get PeriodicEgressEndpoints
    ```

## Retrieve runtime configuration

<!-- MB 9/16: Same deal here--I get an error message that the resource cannot be retrieved. -->

1. Access EdgeCmd utility through the command line.
2. Run the following command:

    ```cmd
    edgecmd get Runtime
    ```
