---
uid: ConfigureEdgeDataStore
---

# Configure Edge Data Store

Use the EdgeCmd utility to configure Edge Data Store.

## Change all values of a facet

Complete the following to change all values of a facet:

1. Access the EdgeCmd utility through a command line tool.
2. Type _edgecmd Configuration_, then the `componentId` and `facetName` followed by key=value pairs, and press Enter.

   **Example:** Change all values in the 'Logging' facet:

   ```bash
   edgecmd Configuration Storage Logging LogLevel=Warning LogFileSizeLimitBytes=32768 LogFileCountLimit=5
   ```

## Configure key=value pairs in a facet

Complete the following to configure any number of valid key=value pairs in a facet:

1. Access the EdgeCmd utility through a command line tool.
2. Type _edgecmd Configuration_, then the `componentId` and `facetName` followed by the key=value pairs, and press Enter.

   **Example:** Change a single value in the 'Logging' facet:

   ```bash
   edgecmd Configuration Storage Logging LogFileCountLimit=5
   ```

## Add an entry to a collection configuration

Complete the following to add an entry to a collection configuration:

1. Access the EdgeCmd utility through a command line tool.
2. Type _edgecmd Configuration_, then the `componentId` and `facetName` followed by the key=value pairs, and press Enter.

   **Example:** Add the 'Health Endpoints' facet to the 'System' component:

   ```bash
   edgecmd Configuration System HealthEndpoints Id=endpoint_1 Endpoint=endpointURL UserName=UserName Password=Password
   ```
	**Note:** If an entry with the specified ID already exists, it will be updated based on the new key=value pairs.

## Configure with JSON Files

Configure Edge Data Store by a JSON file input into the EdgeCmd application. A file import completely replaces the existing configurations; therefore, you cannot use it to change individual values in a facet without modifying others.

### Import bulk configuration

Complete the following to import a bulk configuration:
	
1. Access the EdgeCmd utility through a command line tool.
2. Type the following command, replacing `<PathToJsonFile>` with the path to the file, and press Enter.

   ```bash
   edgecmd Configuration file=<PathToJsonFile>
   ```

### Import facet specific configuration

Complete the following to import a facet specific configuration file for a component:
	
1. Access the EdgeCmd utility through a command line tool.
2. Type the following command, replacing `<componentId>` with the ID of the component, `<facetName>` with the name of the facet, and `<PathToJsonFile>` with the path to the file. Then press Enter.

   ```bash
   edgecmd Configuration <componentId> <facetName> file=<PathToJsonFile>
   ```

### Import facets configuration in bulk

Complete the following steps to import a file with configuration for individual facets as a bulk file import operation:
	**Note:** The file must contain only information for the given component ID. 
	
1. Access the EdgeCmd utility through a command line tool.
2. Type the following command, replacing the file name as shown in the _Bulk_Storage_Runtime.json_ example, and press Enter.

   ```bash
   edgecmd Configuration file="~/Bulk_Storage_Runtime.json"
   ```

   **Example:**

   ```JSON
   {
      		"Storage": {
			"Runtime": {
				"StreamStorageLimitMb": 66,
				"StreamStorageTargetMb": 33,
				"IngressDebugExpiration": "2020-07-08T01:00:00",
				"CheckpointRateInSec": 6,
				"TransactionLogLimitMB": 350,
				"EnableTransactionLog": true
			}
		}
	}
	```

	**Note:** The command only affects the specified key-value pairs for the 'Runtime' facet in the 'Storage' component. It does not change any other components or facets; however, import affects all key-value pairs in the facet. If you import the following example JSON file, the 'StreamStorageLimitMb' and 'StreamStorageTargetMb' values will be modified and the remaining values in the 'Runtime' facet will be reset to their default values (IngressDebugExpiration, CheckpointRateInSec, TransactionLogLimitMB, and EnableTransactionLog).

	```JSON
	{
		"Storage": {
			"Runtime": {
				"StreamStorageLimitMb": 66,
				"StreamStorageTargetMb": 33,
			}
		}
	}
	```
