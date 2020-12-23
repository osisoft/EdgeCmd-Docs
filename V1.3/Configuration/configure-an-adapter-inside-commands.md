---
uid: ConfigureAnAdapterInsideCommands1-3
---

# Configure an adapter inside commands

Use EdgeCmd utility to configure an adapter using only commands or by pointing to JSON files. For more information, see [Configure an adapter with JSON files](xref:ConfigureAnAdapterWithJsonFiles1-3).

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter, you need to add it in the command. For example:

```cmd
edgecmd -port 5591 <RestOfTheCommand>
```

**Note:** If a command contains slashes, you must add escape characters as follows:<br>
  - In *Windows*, add a second slash.<br> 
       Example: `TestUser\OilCompany` becomes `TestUser\\OilCompany`

  - In *Linux*, add three slashes.<br>
       Example: `TestUser\OilCompany` becomes `TestUser\\\\OilCompany`

## Change all values of a facet

Complete the following steps to change all values of a facet:

1. Access EdgeCmd utility through the command line.
2. Type the `set` keyword.
3. Add the `<facetName>`and `<componentId>`, replacing both with their respective values.
4. Add all key=value pairs. Then press Enter.

   ```cmd
   edgecmd set <facetName> -cid <componentId> -<Key1> <Value1> -<Key2> <Value2> -<Key3> <Value3>
   ```

   **Example:** Change all values in the 'Logging' facet of the 'OpcUa1' component:

   ```cmd
   edgecmd set Logging -cid OpcUa1 -LogLevel Warning -LogFileSizeLimitBytes 5000 -LogFileCountLimit 30
   ```

## Configure key=value pairs in a facet

Complete the following steps to configure any number of valid key=value pairs in a facet:

1. Access EdgeCmd utility through the command line.
2. Type the `edit` keyword and the `<facetName>`.
3. Add the `<facetName>`and `<componentId>`, replacing both with their respective values.
4. Add the key=value pairs you want to configure. Then press Enter.

   ```cmd
   edgecmd edit <facetName> -cid <componentId> -<Key1> <Value1>
   ```

   **Example:** Configure the 'LogFileCountLimit' key in the 'Logging' facet of the 'Modbus1' component:

   ```cmd
   edgecmd edit Logging -cid Modbus1 -LogFileCountLimit 15
   ```

## Add an entry to a collection configuration

Complete the following steps to add an entry to a collection configuration:

1. Access EdgeCmd utility through the command line.
2. Type the `add` keyword and the `<facetName>`.
3. Add the `<componentId>`, replacing it with the ID of the component.
4. Add the key=value pairs. Then press Enter.

   ```cmd
   edgecmd add <facetName> -cid <componentId> -<Key1> <Value1> -<Key2> <Value2>
   ```

   **Example:** Add the 'Schedules' facet to the 'Modbus1' component:

   ```cmd
   edgecmd add Schedules -cid Modbus1 -Id 2 -Period 00:00:30
   ```
