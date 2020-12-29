---
uid: ConfigureAnAdapterOrEDSWithJsonFiles1-1
---

# Configure an adapter or EDS with JSON Files

Use EdgeCmd utility to  import a JSON file that contains the adapter or EDS configuration into the adapter or EDS. A file import completely replaces the existing configurations; therefore, you cannot use it to change individual values in a facet without modifying others.

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter or EDS, you need to add it in the command. For example:

```cmd
edgecmd -port 5591 <RestOfTheCommand>
```

## Import bulk configuration

Complete the following steps to import a bulk configuration:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<PathToJsonFile>` with the path to the JSON file that contains the application configuration. Then press Enter.

   ```cmd
   edgecmd set application -file <PathToJsonFile>
   ```

   **Example:**

   ```cmd
   edgecmd set application -file C:\Users\TestUser\Adapter\BulkConfiguration.json
   ```

## Import component configuration

Complete the following steps to import a configuration file for a component:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<componentId>` with the ID of the component and `<PathToJsonFile>` with the path to the JSON file that contains the component configuration. Then press Enter.

   ```cmd
   edgecmd set -cid <componentId> -file <PathToJsonFile>
   ```

   **Example:**

   ```cmd
   edgecmd set -cid OpcUa1 -file C:\Users\TestUser\Adapter\ComponentConfiguration.json
   ```

## Import facet specific configuration

Complete the following steps to import a facet specific configuration file for a component:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<facetName>` with the name of the facet, `<componentId>` with the ID of the component, and `<PathToJsonFile>` with the path to the JSON file that contains the component facet configuration. Then press Enter.

   ```cmd
   edgecmd set <facetName> -cid <componentId> file <PathToJsonFile>
   ```

   **Example:**

   ```cmd
   edgecmd set Logging -cid OpcUa1 file C:\Users\TestUser\Adapter\FacetConfiguration.json
   ```
