---
uid: ConfigureAnAdapterOrEDSWithCommands
---

# Configure an adapter or EDS with commands

Use EdgeCmd utility to configure an adapter or EDS using only commands or by pointing to JSON files. For more information, see [Configure an adapter or EDS with JSON files](xref:ConfigureAnAdapterOrEDSWithJsonFiles).

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter or EDS, you need to add it in the command. For example:

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
4. Add all key-value pairs. Then press Enter.

   ```cmd
   edgecmd set <facetName> -cid <componentId> -<Key1> <Value1> -<Key2> <Value2> -<Key3> <Value3>
   ```

   **Example:** Change all values in the 'Logging' facet of the 'OpcUa1' component:

   ```cmd
   edgecmd set Logging -cid OpcUa1 -LogLevel Warning -LogFileSizeLimitBytes 5000 -LogFileCountLimit 30
   ```

## Configure key-value pairs in a facet

Complete the following steps to configure any number of valid key-value pairs in a facet:

1. Access EdgeCmd utility through the command line.
2. Type the `edit` keyword and the `<facetName>`.
3. Add the `<facetName>`and `<componentId>`, replacing both with their respective values.
4. Add the key-value pairs you want to configure. Then press Enter.

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
4. Add the key-value pairs. Then press Enter.

   ```cmd
   edgecmd add <facetName> -cid <componentId> -<Key1> <Value1> -<Key2> <Value2>
   ```

   **Example:** Add the 'Schedules' facet to the 'Modbus1' component:

   ```cmd
   edgecmd add Schedules -cid Modbus1 -Id 2 -Period 00:00:30
   ```

## Configure payload port

EdgeCmd utility commands may include up to two port numbers. The first specified port number is always designated for the EdgeCmd application. The second port number is designated for the payload of the adapter or EDS.

Complete the following steps to edit the port number of the payload:

1. Access EdgeCmd utility through the command line.
2. Type the `edit` and `datasource` keywords.
3. Add the first `<port>`, replacing it with the port number of the EdgeCmd application. The default is `5590`.
4. Add the `<componentId>`, replacing it with the ID of the component.
5. Add the second `<port>`, replacing it with the port number of the payload. Then press Enter.

```cmd
edgecmd edit datasource -port 5590 -cid Mqtt1 -port 1885
```

**Note:** <br>

- If a payload port number is configured for a component and you specify only one port number in the data source command, you will receive the following error message: `Invalid arguments. Input arguments are required.`
- If you specify more than two port numbers, you will receive the following error message: `Duplicate optional argument: -port`
