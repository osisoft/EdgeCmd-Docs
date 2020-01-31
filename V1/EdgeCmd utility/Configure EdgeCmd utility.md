---
uid: ConfigureEdgeCmdUtility
---

# Configure EdgeCmd utility
The following sections provide instructions for the configuration of EdgeCmd utility for Windows or Linux.

**Note:** The following EdgeCmd utility locations are based on the installation instructions in [EdgeCmd utility](xref:Installedgecmd).

Location on Windows:

```cmd
C:\Program Files\OSIsoft\EdgeCmd\edgecmd.exe
```

**Note:** Specify the full path when you use EdgeCmd on Windows.

Location on Linux:

```bash
 /opt/OSIsoft/EdgeCmd/edgecmd
```

**Note:** You can access EdgeCmd without using the full path on Linux. 

## Adapter configuration with EdgeCmd

Most configuration options that can be done using REST can also be done using the edgecmd utility and command line arguments.

## Get help

The Edgecmd application provides a 'Help' utility. For general instructions on how to use the Edgecmd application, type:

```bash
edgecmd Help
```

You can also use the utility to get help for any registered component in the adapter. If you add a specific component ID to the end of the previous command, you receive help output for every configuration facet that the component supports, along with examples of commands that you can run to configure the component.

Example: View help for the 'System' component:

```
edgecmd Help System
---------------------------------------------------------------------------------------------------------
Component System command-line options => 'Logging'
---------------------------------------------------------------------------------------------------------
LogLevel                    [Required] Desired log level settings. Options: Trace, Debug, Information, Warning, Error, Critical, None.
LogFileSizeLimitBytes       [Required] Maximum size in bytes of log files that the service will create for this component. Must be no less than 1000.
LogFileCountLimit           [Required] Maximum number of log files that the service will create for this component. Must be a positive integer.

Example: ./edgecmd Configuration System Logging LogLevel=Warning
Example: ./edgecmd Configuration System Logging LogFileSizeLimitBytes=32768
Example: ./edgecmd Configuration System Logging LogFileCountLimit=5


---------------------------------------------------------------------------------------------------------
Component System command-line options => 'HealthEndpoints'
---------------------------------------------------------------------------------------------------------
Id                           [Optional] Id of existing configuration to be edited or removed.
Endpoint                     [Required] URL of OMF destination
UserName                     [Required group 1]  User name used for authentication to PI Web API OMF endpoint.          
Password                     [Required group 1]  Password used for authentication to PI Web API OMF endpoint.
ClientId                     [Required group 2]  Client ID used for authentication to OSIsoft Cloud Services.
ClientSecret                 [Required group 2]  Client Secret used for authentication to OSIsoft Cloud Services.
TokenEndpoint                [Optional group 2] URL of OMF destination's token service.
ValidateEndpointCertificate  [Optional] If true, endpoint certificate will be validated (recommended). If false, any endpoint certificate will be accepted. OSIsoft strongly recommends using disabled endpoint certificate validation for testing purposes only.

Note: Only one Required group must be specified. Group 1 for PI Web API or Group 2 for OCS.
Example:
Add a new endpoint:
  ./edgecmd Configuration System HealthEndpoints Endpoint=endpointURL UserName=UserName Password=Password
Update fields of an existing endpoint:
  ./edgecmd Configuration System HealthEndpoints Id=Endpoint1 Password=newPassword
View existing endpoints:
  ./edgecmd Configuration System HealthEndpoints
File Import (replaces current endpoints):
  ./edgecmd Configuration System HealthEndpoints File=endpoints.json
Delete an endpoint:
  ./edgecmd Configuration System HealthEndpoints Id=Endpoint1 Delete

---------------------------------------------------------------------------------------------------------
Component System command-line options => 'Diagnostics'
---------------------------------------------------------------------------------------------------------
EnableDiagnostics                       [Required] Enable global diagnostics.

Example: ./edgecmd Configuration System Diagnostics EnableDiagnostics=True


---------------------------------------------------------------------------------------------------------
Component System command-line options => 'Components'
---------------------------------------------------------------------------------------------------------
ComponentId                        [Required] ID of the hosted component.
ComponentType                      [Required] Type of the hosted component.

Example: ./edgecmd Configuration System Components ComponentId=Modus1 ComponentType=Modbus


---------------------------------------------------------------------------------------------------------
Component System command-line options => 'Buffering'
---------------------------------------------------------------------------------------------------------
BufferLocation                 Location of the on-disk buffers
MaxBufferSizeMB                Maximum size of the on-disk buffers (-1 = restricted only by available free disk space)
EnableBuffering                Enable or disable buffering
```

For help regarding a specific facet within a component, add the facet name after the component ID.

Example: Help for the 'Diagnostics' facet within the 'System' component:

```
edgecmd Help System Diagnostics

---------------------------------------------------------------------------------------------------------
Component System command-line options => 'Diagnostics'
---------------------------------------------------------------------------------------------------------
EnableDiagnostics                       [Required] Enable global diagnostics.

Example: ./edgecmd Configuration System Diagnostics EnableDiagnostics=True
```

## Adapter components
The EdgeCmd utility enables you to add, configure, and delete Adapter components.

### Add components
With the following command, you can view which components are currently configured on the adapter:

```bash
edgecmd Configuration System Components
```

To register a new component, use the following command:

```bash
edgecmd Configuration System Components componentId=<componentId> componentType=<componentType>
```

The only valid component type is the Adapter Type. For example, ff you are trying to register a new Modbus component, use "Modbus" and if you are trying to register an OPC UA component, use "OpcUa". Refer to the specific Adapter's user guide for that adapter's component type. 

Example: Modbus adapter component registration:

```bash
edgecmd Configuration System Components componentId=Modbus1 componentType=Modbus
```

### Configure components

The adapters have configurable facets. They may include data source, data selection, and logging. You can configure these with edgecmd by specifying a component ID and facet name. 

Example: Configuration of the data source facet of a Modbus adapter:

```bash
edgecmd Configuration Modbus1 DataSource IpAddress=117.23.45.110 port=502 ConnectTimeout=15000 StreamIdPrefix="DataSource1"
```

For detailed information on how to configure each adapter, see the user guide for the corresponding adapter.

### Delete components

You can delete components from the adapter by using the following command:

```bash
edgecmd Configuration System Components id=<componentId> delete
```

**Note:** You can't delete the "Egress" component because it is required for the adapter to operate.


## Retrieve existing system configuration

You can use the edgecmd utility to view the configuration for each part of the adapter.

To view the entire configuration for every system component, run the following command:

```bash
edgecmd Configuration
```

To retrieve component specific configuration:

```bash
edgecmd Configuration componentId
```

To retrieve facet specific configuration of an adapter component:

```bash
edgecmd Configuration componentId facetName
```

For facets that contain multiple entries, you can retrieve the configuration for a specific entry by its Id:

```bash
edgecmd Configuration componentId facetName id=IndexToRetrieve
```

### Examples

- View all configurations of the adapter using edgecmd:

```
edgecmd configuration
{
  "System": {
    "Logging": {
      "logLevel": "Information",
      "logFileSizeLimitBytes": 34636833,
      "logFileCountLimit": 31
    },
    "HealthEndpoints": [],
    "Diagnostics": {
      "enableDiagnostics": true
    },
    "Components": [
      {
        "componentId": "Modbus1",
        "componentType": "Modbus"
      },
      {
        "componentId": "Egress",
        "componentType": "OmfEgress"
      }
    ],
    "Buffering": {
      "bufferLocation": "C:/ProgramData/OSIsoft/Adapters/Modbus/Modbus/Buffers",
      "maxBufferSizeMB": -1,
      "enableBuffering": true
    }
  },
  "Modbus1": {
    "Logging": {
      "logLevel": "Information",
      "logFileSizeLimitBytes": 34636833,
      "logFileCountLimit": 31
    },
    "DataSource": {},
    "DataSelection": []
  },
  "Egress": {
    "Logging": {
      "logLevel": "Information",
      "logFileSizeLimitBytes": 34636833,
      "logFileCountLimit": 31
    },
    "DataEndpoints": [],
    "Buffering": {
      "onDiskBufferLocation": "C:/ProgramData/OSIsoft/Adapters/Modbus/Modbus/Buffers",
      "onDiskMaxBufferSizeMB": -1
    }
  }
}
```

- View the configuration of the 'System' component
```
edgecmd Configuration System
{
  "Logging": {
    "logLevel": "Information",
    "logFileSizeLimitBytes": 34636833,
    "logFileCountLimit": 31
  },
  "HealthEndpoints": [],
  "Diagnostics": {
    "enableDiagnostics": true
  },
  "Components": [
    {
      "componentId": "Modbus1",
      "componentType": "Modbus"
    },
    {
      "componentId": "Egress",
      "componentType": "OmfEgress"
    }
  ],
  "Buffering": {
    "bufferLocation": "C:/ProgramData/OSIsoft/Adapters/Modbus/Modbus/Buffers",
    "maxBufferSizeMB": -1,
    "enableBuffering": true
  }
}
```

- View the configuration for the 'Logging' facet within the 'Egress' component
```
edgecmd Configuration Egress Logging
{
  "logLevel": "Information",
  "logFileSizeLimitBytes": 34636833,
  "logFileCountLimit": 31
}
```

- View the configuration of a specific entry in the 'healthendpoints' facet within the 'System' component
```
edgecmd configuration system healthendpoints id=Endpoint_1
{
  "id": "Endpoint_1",
  "endpoint": "https://localhost:5821",
  "userName": "user_54",
  "password": "***************",
  "clientId": null,
  "clientSecret": null,
  "tokenEndpoint": null,
  "validateEndpointCertificate": true
}
```

## Configure Adapter

To create a configuration, you must enter the component and facet where the configuration payload should go, followed by key=value pairs to specify which values are to be changed. 

Example: Change all values in the 'Logging' facet:

```bash
edgecmd Configuration Egress Logging LogLevel=Warning LogFileSizeLimitBytes=32768 LogFileCountLimit=5
```

You can use this to configure any number of valid key=value pairs in a facet.

Example: Change a single value in the 'Logging' facet:

```bash
edgecmd Configuration Egress Logging LogFileCountLimit=5
```

You can also use it to add an entry to a collection configuration, for example, the 'Health Endpoints' facet in the 'System' component:

```bash
edgecmd Configuration System HealthEndpoints Id=endpoint_1 Endpoint=endpointURL UserName=UserName Password=Password
```
**Note:** If an entry with the specified id already exists, it will be updated based on the new key=value pairs.

### Configure with JSON Files
You can also configure the adapter by a JSON file input into the edgecmd application. File imports will completely replace the existing configurations that you are attempting to change. Therefore, it cannot be used to change individual values in a facet without modifying others.

To import a bulk configuration:
```bash
edgecmd Configuration file=PathToJsonFile
```

To import a facet specific configuration file for a component:
```
edgecmd Configuration componentId facetName file=PathToJsonFile
```

To import a file with configuration for individual facets, you can use a bulk file import operation. The file must contain just payload for the given component ID. 

Example command:

```bash
edgecmd Configuration file="~/Logging.json"
```

The file 'dataEndpoints.json' contains:
```JSON
{
	"Egress": {
		"Logging": {
		  "logLevel": "Warning",
      "logFileSizeLimitBytes": 19283,
      "logFileCountLimit": 999
		}
	}
}
```
The command will only affect the 'Logging' facet in the 'Egress' component, it will not change any other components or facets. If you import a file containing the following, the 'logLevel' and 'logFileSizeLimitBytes"' values would be modified, resetting the remaining values in the facet (logFileSizeLimitBytes) to their default values:
```JSON
{
	"Egress": {
		"Logging": {
		  "logLevel": "Warning",
		  "logFileSizeLimitBytes": 19283
		}
	}
}
```

## Delete configuration data

You can use the edgecmd application to delete configuration data from Edge Data Store.
To delete a configuration entry from a collection configuration (for example, 'HealthEndpoints' facet within the 'System' component), you must specify the component ID, facet, and ID of the entry to remove followed by the 'delete' keyword.
Example:
```bash
edgecmd Configuration System HealthEndpoints Id=endpoint_1 delete
```

To delete an entire configuration file, you must specify the component ID and facet followed by the 'delete' keyword.
Example:
```bash
edgecmd Configuration System HealthEndpoints delete
```
# Administration Commands

There are two administrative commands, which will either start or stop a component. Only adapter components can be started or stopped. 

```
  ./edgecmd Administration ComponentId Stop
  ./edgecmd Administration ComponentId Start
```
