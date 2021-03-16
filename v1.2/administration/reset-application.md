---
uid: ResetApplication1-2
---

# Reset application

Use EdgeCmd utility to reset the entire application and the storage in EDS.

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter or EDS, you need to add it in the command. For example:

```cmd
edgecmd -port 5591 <RestOfTheCommand>
```

1. Access EdgeCmd utility through the command line.
2. Run the following command:

    ```cmd
    edgecmd reset application
    ```

3. Answer prompt to confirm the reset.

    **Note:** You can specify the `-y` parameter in the command to skip the confirmation prompt.
