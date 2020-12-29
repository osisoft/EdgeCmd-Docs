---
uid: StartOrStopAComponent1-2
---

# Start or stop a component

Complete the following steps to either start or stop an adapter or EDS component.

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter or EDS, you need to add it in the command. For example:

```cmd
edgecmd -port 5591 <RestOfTheCommand>
```

1. Access EdgeCmd utility through the command line.
2. Type one of the following in the command line, replacing `<componentId>` with the ID of the component, and press Enter.

   -  ```cmd
      edgecmd stop -cid <ComponentId>
      ```

      **Example - Stop the OpcUa1 component**

      ```cmd
      edgecmd stop -cid OpcUa1
      ```
  
   -  ```cmd
      edgecmd start -cid <ComponentId>
      ```

      **Example - Start the OpcUa1 component**

      ```cmd
      edgecmd start -cid OpcUa1
      ```
