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

Complete the following steps to retrieve EDS's storage component configuration:

1. Access EdgeCmd utility through the command line.
2. Run the following command:

    ```cmd
    edgecmd get -cid Storage
    ```

## Retrieve periodic egress endpoints configuration

Complete the following steps to retrieve EDS's periodic egress endpoint configuration:

1. Access EdgeCmd utility through the command line.
2. Run the following command:

    ```cmd
    edgecmd get PeriodicEgressEndpoints
    ```

## Retrieve runtime configuration

Complete the following steps to retrieve EDS's runtime configuration:

1. Access EdgeCmd utility through the command line.
2. Run the following command:

    ```cmd
    edgecmd get Runtime
    ```
