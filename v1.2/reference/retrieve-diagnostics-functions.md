---
uid: RetrieveDiagnosticsFunctions1-2
---

# Retrieve diagnostics functions

Use EdgeCmd utility to retrieve diagnostics functions of the platform and components.

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter, you need to add it in the command. For example:

```cmd
edgecmd -port 5591 <RestOfTheCommand>
```

## Retrieve diagnostics

1. Access EdgeCmd utility through the command line.
2. Run the following command:

    ```cmd
    edgecmd get Diagnostics
    ```

    <details>
    <summary>Sample output</summary>
    <pre>

        {
            "timestamp": "2020-07-15T18:27:59.4804167Z",
            "processIdentifier": 5744,
            "startTime": "2020-07-20T21:26:45.9662964Z",
            "workingSet": 41.90625,
            "totalProcessorTime": 137.578125,
            "totalUserProcessorTime": 73.53125,
            "totalPrivilegedProcessorTime": 64.046875,
            "threadCount": 23,
            "handleCount": 628,
            "managedMemorySize": 8.916587829589844,
            "privateMemorySize": 49.54296875,
            "peakPagedMemorySize": 57.21484375,
            "storageTotalSize": 486699.0859375,
            "storageFreeSpace": 365912.98828125
        }

    </pre>
    </details>

## Retrieve version

1. Access EdgeCmd utility through the command line.
2. Run the following command:

    ```cmd
    edgecmd get Version
    ```

    <details>
    <summary>Sample output</summary>
    <pre>

        {
            "Application Version": "1-2.0.234",
            ".Net Core Version": ".NET Core 3.1.5",
            "Operating System": "Microsoft Windows 10.0.18363"
        }

    </pre>
    </details>
