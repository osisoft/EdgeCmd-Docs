---
uid: Edgecmd commands
---

# EdgeCmd commands

The following tables provide an overview of available edgecmd commands that you can use with components of the adapter. Every command that you use with the edgecmd utility has to be preceded by `edgecmd`.

## Help

| edgecmd command | Description | Examples |
|-----------------|-------------|----------|
|`edgecmd Help`| Display general instructions on how to use the edgecmd utility. | 
|`edgecmd Help <componentName>`| Display help for a specific adapter component. | `edgecmd Help System`|
|`edgecmd Help <componentName> <facetName>`| Display help for a specific facet of an adapter component. | `edgecmd Help System Components`|


## Configuration

### System

| edgecmd command | Description | Examples |
|-----------------|-------------|----------|
|`edgecmd Configuration`| Display the entire configuration for every adapter component. |
|`edgecmd Configuration System Components` | Display the components that are currently configured. | 
|`edgecmd Configuration System Components componentId=<componentId> componentType=<componentType>` | Add a new component.  | `edgecmd Configuration System Components componentId=Modbus1 componentType=Modbus`|
|`edgecmd Configuration System Components id=<componentId> delete` | Delete a component. | `edgecmd Configuration System Components id=Modbus1 delete` |

### Components
| edgecmd command | Description | Examples |
|-----------------|-------------|----------|
|`edgecmd Configuration <componentId>` | Display component specific configuration. | `edgecmd Configuration System` |
|`edgecmd Configuration <componentId> <facetName>` | Display facet specific configuration of an Edge Data Store component. |  `edgecmd Configuration System Logging`|
|`edgecmd Configuration <componentId> <facetName> id=<IndexToRetrieve>`| Display the configuration of specific entry of a facet. | `edgecmd Configuration System HealthEndpoints id=Endpoint1` |
|`edgecmd Configuration <componentId> DataSource` | Configure the data source for the adapter. | For examples, see the adapter's user guide. |
|`edgecmd Configuration <componentId> DataSelection` | Configure the data selection for the adapter. | For examples, see the adapter's user guide. |
|`edgecmd Configuration <componentId> Logging` | Configure logging for a component. | For examples, see [Logging configuration](xref:LoggingConfiguration).|

## Configuration with JSON files
| edgecmd command | Description | Examples |
|-----------------|-------------|----------|
| `edgecmd Configuration file=<PathToJsonFile>` | Import a bulk configuration through a JSON file. | `edgecmd Configuration file="~/Bulk_Storage_Runtime.json"`|
| `edgecmd Configuration <componentId> <facetName> file=<PathToJsonFile>` | Import a facet specific configuration file for a component. | `edgecmd Configuration System Logging file="~/System_Logging.json"`|

# Administraton
| edgecmd command | Description | Examples |
|-----------------|-------------|----------|
| `edgecmd Administration ComponentId Stop` | Stops a component. Only applicable for adapter type components. | `edgecmd Administration Modbus1 Stop`|
| `edgecmd Administration ComponentId Start` | Starts a component. Only applicable for adapter type components. | `edgecmd Administration Modbus1 Start`|
