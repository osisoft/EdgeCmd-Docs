---
uid: EdgeCmdCommands
---

# EdgeCmd commands

The tables in the following sections provide a description of every command available in EdgeCmd utility. The following rules apply:

- Every command has to be preceded by `edgecmd`.
- All parts of a command that are wrapped in `[ ]` are optional and do not need to be specified.
- The `-y` keyword in a command confirms overwriting of an existing file.

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter, you need to add it in the command. For example:

```cmd
edgecmd -port 5591 Configuration <RestOfTheCommand>
```

**Note:** If a command contains slashes, you must add escape characters as follows:<br>

  - In *Windows*, add a second slash.<br> 
       Example: `TestUser\OilCompany` becomes `TestUser\\OilCompany`

  - In *Linux*, add three slashes.<br>
       Example: `TestUser\OilCompany` becomes `TestUser\\\\OilCompany`

## Help output

The following commands display help output for different levels of the application.

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd help` | Display help output for the EdgeCmd application.
`edgecmd help [<target>]` | Display configuration help output for System level targets, for example `application`, `healthendpoints`, and `logging`. | `edgecmd help General`
`edgecmd  help <target> -cid <componentId>` | Display configuration help output for any registered component and facet.  | `edgecmd help DataSource -cid opcua1`
`edgecmd help -cid <componentId>` | Display configuration help output for any registered component. | `edgecmd help -cid OpcUa1`

## Port configuration

EdgeCmd command| Description | Example |
---------------|-------------|----------|
`edgecmd -port 5590 <command> [-cid <componentId>]` | Specify the port number for communication with EDS or the adapter. The default is `5590`. | `edgecmd -port 5595 get Components`
`edgecmd -port 5590 <command> [-cid <componentId>] -port <port>` | Specify the port number for the adapter or EDS payload.<br><br>For more information on how to configure a payload port number, see [Configure an adapter or EDS with commands](xref:ConfigureAnAdapterOrEDSWithCommands#configure-payload-port). | `edgecmd -port 5590 edit datasource -cid Mqtt1 -port 1885`

## Application configuration

The following commands configure the application.

EdgeCmd command| Description | Example |
---------------|-------------|----------|
`edgecmd get Application [-file <filepath>]` | Get the configuration for every platform component. | `edgecmd get Application`
`edgecmd set Application -file <filepath>` | Import the entire configuration for a AVEVA adapter or EDS. | `edgecmd set Application -file C:\Users\TestUser\Adapter\Configuration.json`
`edgecmd reset Application`  | Reset the entire application and storage in EDS. |
`edgecmd help Application` | Display help output for the application target.

## System component configuration

The following commands configure specific facets of the system component.

### Components facet configuration

EdgeCmd command| Description | Example |
---------------|-------------|----------|
`edgecmd get Components [-file <filepath>]` | Get the component configuration. | `edgecmd get Components`
`edgecmd set Components [-file <filepath>]` | Import the components configuration. | `edgecmd set Components -file C:\Users\TestUser\Components\Configuration.json`
`edgecmd add Components [-type <type>] [-id <componentId>]`  | Add a component to the components configuration. | `edgecmd add Components  -type Modbus -id Modbus1`
`edgecmd remove Components [-id <componentId] [-y]` | Remove the specified component from the configuration. | `edgecmd remove Components -id Modbus1`
`edgecmd help Components`| Display help output for the components configuration. |

### Buffering facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get Buffering [-file <filepath>]` | Get the buffering configuration. | `edgecmd get Buffering -file C:\Users\TestUser\Buffering\Configuration.json`
`edgecmd set Buffering [-file <filepath>]` | Import the buffering configuration. | `edgecmd set Buffering`
`edgecmd edit Buffering [-bufferLocation <value>] [-maxBufferSizeMB <value>] [-enableBuffering <value>]`  | Change the buffering configuration. | `edgecmd Buffering -bufferLocation C:/ProgramData/OSIsoft/Adapters/Modbus/Buffers -maxBufferSizeMB 1024 -enableBuffering true`
`edgecmd help Buffering` | Display help output for the buffering configuration.

### Health endpoints facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get HealthEndpoints [-file <filepath>]` | Get the health endpoints configuration. | `edgecmd get HealthEndpoints`
`edgecmd set HealthEndpoints [-file <filepath>]` | Import the health endpoints configuration. | `edgecmd set HealthEndpoints -file C:\Users\TestUser\HealthEndpoints\Configuration.json`
`edgecmd add HealthEndpoints [-id <string>] [-Endpoint <endpointUrl>] [-UserName <userName>] [-Password <password>] [-ClientId <clientId>] [-ClientSecret <clientSecret>] [-TokenEndpoint <tokenEndpoint>] [-ValidateEndpointCertificate <true/false>]`  | Add a health endpoint. | `edgecmd add HealthEndpoints -id OCS -Endpoint https://OCS_OMF_endpoint -ClientId TestUser -ClientSecret TestPassword`
`edgecmd edit HealthEndpoints [-id <string>] [-Endpoint <endpointUrl>] [-UserName <userName>] [-Password <password>] [-ClientId <clientId>] [-ClientSecret <clientSecret>] [-TokenEndpoint <tokenEndpoint>] [-ValidateEndpointCertificate <true/false>]` | Change a health endpoint. | `edgecmd edit HealthEndpoints -id OCS -Endpoint https://OCS_OMF_endpoint -ClientId TestUser -ClientSecret TestPassword`
`edgecmd remove HealthEndpoints [-id <string>] [-y]`| Remove a health endpoint. | `edgecmd remove HealthEndpoints -id OCS`
`edgecmd help HealthEndpoints` | Display help output for the health endpoints configuration.

## OMF egress data endpoints facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get DataEndpoints [-file <filepath>]` | Get the data endpoints configuration. | `edgecmd get DataEndpoints`
`edgecmd set DataEndpoints [-file <filepath>]` | Import the data endpoints configuration. | `edgecmd set DataEndpoints -file C:\Users\TestUser\DataEndpoints\Configuration.json`
`edgecmd add DataEndpoints [-id <endpointId>] [-Endpoint <endpointUrl>] [-UserName <userName>] [-Password <password>] [-ClientId <clientId>] [-ClientSecret <clientSecret>] [-TokenEndpoint <tokenEndpoint>] [-ValidateEndpointCertificate <true/false>]`  | Add data endpoints. | `edgecmd add DataEndpoints -id PI Web Api  -Endpoint https://pi_web_api_server/piwebapi/omf/ -UserName TestUser -Password TestPassword -ValidateEndpointCertificate false`
`edgecmd edit DataEndpoints -id <string> [-Endpoint <endpointUrl>] [-UserName <userName>] [-Password <password>] [-ClientId <clientId>] [-ClientSecret <clientSecret>] [-TokenEndpoint <tokenEndpoint>] [-ValidateEndpointCertificate <true/false>]` | Change a data endpoint. | `edgecmd edit DataEndpoints -id PI Web Api -Endpoint https://pi_web_api_server/piwebapi/omf/ -UserName TestUser -Password TestPassword -ValidateEndpointCertificate true` |
`edgecmd remove DataEndpoints -id <string> [-y]`| Remove the specified data endpoint. | `edgecmd remove DataEndpoints -id PI Web API`
`edgecmd remove DataEndpoints [-y]`| Remove all data endpoints. | `edgecmd remove DataEndpoints -y`
`edgecmd help DataEndpoints`| Display help output for the data endpoints configuration.

## Component configuration

The following commands configure a component.

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get -cid <componentId> [-file <filepath>]` | Get the configuration of the specified component. | `edgecmd get -cid OpcUa1`
`edgecmd set -cid <componentId> -file <filepath>` | Import the configuration for a component. | `edgecmd set -cid Modbus1 -file C:\Users\TestUser\Components\Configuration.json`
`edgecmd remove -cid <componentId> [-y]`  | Remove the specified component. | `edgecmd remove -cid OpcUa1 -y`
`edgecmd start -cid <componentId>` | Start the specified component. | `edgecmd start -cid Modbus1`
`edgecmd stop -cid <componentId>`| Stop the specified component. | `edgecmd stop -cid OpcUa1`
`edgecmd help -cid <componentId>` | Display help output for the specified component. | `edgecmd help -cid Modbus1`

## Component facets configuration

The following commands configure specific facets of a component.

### Logging facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get Logging [-cid <componentId>] [-file <filepath>]` | Get the logging configuration for specified component. | `edgecmd get Logging -cid Modbus1`
`edgecmd set Logging [-cid <componentId>] [-file <filepath>]` | Import the logging configuration of the specified component. | `edgecmd set Logging -cid OpcUa1`
`edgecmd edit Logging [-cid <componentId>] [-LogLevel <logLevel>] [-LogFileSizeLimitBytes <MaxSize>] [-LogFileCountLimit <FileCount>]`  | Change the logging configuration for the specified component. | `edgecmd edit Logging -cid Modbus1 -LogLevel Information -LogFileSizeLimitBytes 4567 -LogFileCountLimit 123`
`edgecmd help Logging` | Display help output for the logging facet. |

### Schedules facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get Schedules -cid <componentId> [-file <filepath>]` | Get the schedules configuration for the specified component. | `edgecmd get Schedules -cid Modbus1`
`edgecmd set Schedules -cid <componentId> [-file <filepath>]` | Import the schedules configuration for the specified component. | `edgecmd set Schedules -cid OpcUa1 -file C:\Users\TestUsers\Schedules\Configuration.json`
`edgecmd add Schedules -cid <componentId> -id <itemid> [-Period <period>] [-Offset <offset>]`  | Add the schedules configuration for the specified component. | `edgecmd add Schedules -cid Modbus1 -id Schedule1 -Period 125 -Offset 25`
`edgecmd edit Schedule -cid <componentId> -id <itemid> [-Period <period>] [-Offset <offset>]` | Change the schedules configuration for the specified component. | `edgecmd edit Schedule -cid OpcUa1 -id Schedule2`
`edgecmd remove Schedule -cid <componentId> [-id <itemid>] [-y]`| Remove the schedules configuration for an item in the specified component. | `edgecmd remove Schedule -cid Modbus1 -id Schedule3 -y`
`edgecmd remove Schedule -cid <componentId> [-y]` | Remove the schedules configuration for the specified component. | `edgecmd remove Schedule -cid OpcUa1`
`edgecmd help Schedule –cid <componentId>`| Display help output for the schedules facet. | `edgecmd help Schedule -cid Modbus1`

### Data filters facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get DataFilters -cid <componentId> [-file <filepath>]` | Get the data filters configuration for the specified component. | `edgecmd get DataFilters -cid OpcUa1`
`edgecmd set DataFilters -cid <componentId> [-file <filepath>]` | Import the data filters configuration for the specified component. | `edgecmd set DataFilters -cid Modbus1 -file C:\Users\TestUser\DataFilters\Configuration.json`
`edgecmd add DataFilters -cid <componentId> -id <itemid> [-AbsoluteDeadband <value>] [-PercentChange <value>] [-ExpirationPeriod <value>]`  | Add the data filters configuration for the specified component. | `edgecmd add DataFilters -cid OpcUa1 -id DuplicateData -AbsoluteDeadband 0 -PercentChange 35`
`edgecmd edit DataFilters -cid <componentId> -id <itemid> [-AbsoluteDeadband <value>] [-PercentChange <value>] [-ExpirationPeriod <value>]` | Change the data filters configuration for the specified component. | `edgecmd edit DataFilters -cid Modbus1 -id DuplicateData -AbsoluteDeadband 3 -PercentChange 35`
`edgecmd remove DataFilters -cid <componentId> [-id <itemid>] [-y]`| Remove the data filters configuration for an item in the specified component. | `edgecmd remove DataFilters -cid OpcUa1 -y`
`edgecmd help DataFilters –cid <componentId>` | Display help output for the data filters facet. | `edgecmd help DataFilters -cid Modbus1`

### Data source facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get DataSource -cid <componentId>` | Get the data source configuration for the specified component. | `edgecmd get DataSource -cid OpcUa1`
`edgecmd set DataSource -cid <componentId> [-file <filepath>]` | Import the data source configuration for the specified component. | `edgecmd set DataSource -cid Modbus1 -file C:\Users\TestUser\DataSource\Configuration.json`
`edgecmd set DataSource -cid <componentId> [-<adapterSpecificParameter> <value>]`  | Import the data source configuration parameter for the specified component. | `edgecmd set DataSource -cid OpcUa1 -UseSecureConnection true`
`edgecmd edit DataSource -cid <componentId> [-<adapterSpecificParameter> <value>]` | Change the data source configuration parameter for the specified component. | `edgecmd edit DataSource -cid Modbus1 -UseSecureConnection false`
`edgecmd remove Datasource -cid <componentId> [-y]`| Remove the data source configuration for the specified component. | `edgecmd remove Datasource -cid OpcUa1 -y`
`edgecmd help Datasource -cid <componentId>` | Display the help output for the data source facet. | `edgecmd help Datasource -cid Modbus1`

### Data selection facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get DataSelection -cid <componentId> [-file <filepath>]` | Get the data selection configuration for the specified component. | `edgecmd get DataSelection -cid Modbus1 -file C:\Users\TestUser\DataSelection\Configuration.json`
`edgecmd set DataSelection -cid <componentId> [-file <filepath>]` | Import the data selection configuration for the specified component. | `edgecmd set DataSelection -cid OpcUa1`
`edgecmd get DataSelection -cid <componentId> [-file <filepath>] -csv` | Display the data selection configuration for the specified component in CSV format. | `edgecmd get DataSelection -cid Modbus1 -file C:\Users\TestUser\DataSelection\Configuration.csv -csv`
`edgecmd set DataSelection -cid <componentId> [-file <filepath>] -csv` | Import the data selection configuration for the specified component in CSV format. | `edgecmd set DataSelection -cid OpcUa1 -csv`
`edgecmd add  DataSelection -cid <componentId> -id <itemid>] [-<adapterSpecificParameter> <value>]`  | Add the data selection configuration for the specified component. | `edgecmd add DataSelection -cid OpcUa1 -id Custom1 -Name RandomName`
`edgecmd edit DataSelection -cid <componentId> [-id <itemid>] [-<adapterSpecificParameter> <value>]` | Change the data selection configuration for the specified component. | `edgecmd edit DataSelection -cid Modbus1 -Selected true`
`edgecmd remove  DataSelection -cid <componentId> [-id <itemid>] [-y]`| Remove the data selection configuration for an item in the specified component. | `edgecmd remove DataSelection -cid OpcUa1 -id Random1`
`edgecmd remove DataSelection -cid <componentId> [-y]` | Remove the data selection configuration for the specified component. | `edgecmd remove DataSelection -cid Modbus1 -y`
`edgecmd help DataSelection -cid <componentId>`| Display help output for data selection facet. | `edgecmd help DataSelection -cid OpcUa1`

### General facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get <FacetName> -cid <componentId> [-file <filepath>]` | Get the configuration for the specified facet in the specified component. | `edgecmd get Logging -cid Modbus1`
`edgecmd set <FacetName> -cid <componentId> [-file <filepath>]` | Import the configuration for the specified facet in the specified component. | `edgecmd set DataFilters -cid OpcUa1`
`edgecmd add <FacetName> -cid <componentId> [-<facetSpecificParameter> <value>]`  | Add the configuration for the specified facet in the specified component. | `edgecmd add Logging -cid Modbus1 -LogFileCountLimit 30`
`edgecmd edit <FacetName> -cid <componentId> [-<facetSpecificParameter> <value>]` | Change the configuration for the specified facet in the specified component. | `edgecmd edit DataFilters -cid OpcUa1 -AbsoluteDeadband 0`
`edgecmd remove <FacetName> -cid <componentId> [-y]`| Remove the configuration for the specified facet in the specified component. | `edgecmd remove Logging -cid Modbus1 -y`
`edgecmd help <FacetName> -cid <componentId>` | Display help out output for the specified facet in specified component. | `edgecmd help DataFilters -cid OpcUa1`

## EDS configuration

### Storage configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get Storage` | Get the Storage configuration. |
`edgecmd set Storage [-file <string>]` | Import the Storage configuration. | `edgecmd set Storage -file C:\Users\TestUser\Storage\Configuration.json`
`edgecmd reset Storage [-y]` | Reset the Storage configuration. | `edgecmd reset Storage -y`
`edgecmd help Storage`| Display help output for the Storage configuration. |

### Runtime configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get Runtime` | Get the runtime configuration. |
`edgecmd set Runtime [-file <filepath>]` | Import the runtime configuration. | `edgecmd set Runtime -file C:\Users\TestUser\Runtime\Configuration.json`
`edgecmd edit Runtime [-parameter <value>]`  | Change the runtime configuration. | `edgecmd edit Runtime`
`edgecmd help Runtime` | Display help output for the runtime configuration.

## Diagnostics configuration

EdgeCmd command| Description |
---------------|-------------|
`edgecmd get Diagnostics` | Get the diagnostics configuration. |
`edgecmd get Version` | Get the version information. |
`edgecmd get FailoverState` | Get the failover state information. |

## Data discovery configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd add discoveries -cid <componentId>` | Start a new discovery operation for the specified component and return the status object containing the generated Id of the discovery. | `edgecmd add discoveries -cid Mqtt1`|
`edgecmd get discoveries -cid <componentId>` | Get the active and completed discovery status information for the specified component. | `edgecmd get discoveries -cid Mqtt1`|
| `edgecmd get discoveries -cid <componentId> -id <discoveryId> -result [-csv] [-file <filename>]` | Get the result of the specified discovery for the specified component. | `edgecmd get discoveries -cid Mqtt1 -id 1 -result` |
| `edgecmd add discoveries -cid <componentId> -query "<queryFilter>" -id <discoveryId>` | Start a new discovery operation for the specified component with the specified query. | `edgecmd add discoveries -cid Mqtt1 -query "+/+/Device90" -id 1` |
| `edgecmd get discoveries -cid <componentId> -id <discoveryId> -result -query diff=<discoveryId> [-csv]` | Get the differences between two specified discoveries of the specified component | `edgecmd get discoveries -cid Mqtt1 -id 1 -result -query diff=2` |
| `edgecmd add dataselection -cid <componentId> -select -query discoveryId=<discoveryId>` | Add the specified discovery result to the data selection and set all items to be selected. | `edgecmd add dataselection -cid Mqtt1 -select -query discoveryId=1` |
| `edgecmd get dataselection -cid <componentId> -query diff=<discoveryId> [-csv]` | Compare the data selection against a discovery result. | `edgecmd get dataselection -cid Mqtt1 -query diff=2` |
| `edgecmd  remove discoveries -cid <componentId> -id <discoveryId> -result [-y]` | Remove only the result of the specified discovery from the specified component and cancel discovery if active. | `edgecmd  remove discoveries -cid Mqtt1 -id 2 -result -y`|
| `edgecmd  remove discoveries -cid <componentId> -id <discoveryId> [-y]` | Remove the discovery state and result from the specified component and cancel discovery if active. | `edgecmd  remove discoveries -cid Mqtt1 -id 2 -y`|
| `edgecmd cancel discoveries -cid <componentId> -id <discoveryId>` | Cancel the discovery for the specified component. | `edgecmd cancel discoveries -cid Mqtt1 -id 2` 

## History recovery configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
| `edgecmd add historyrecoveries -cid <componentId> -StartTime <time>` | Start the history recovery for the specified component. | `edgecmd add historyrecoveries -cid Mqtt1 -StartTime 2021-01-09T05:55:00.0` |
| `edgecmd delete historyrecoveries -cid <componentId> -id <historyRecoveryId>` | Cancel the history recovery for the specified component and delete its state. | `edgecmd delete historyrecoveries -cid Mqtt1 -id HistoryRecovery1` | 
| `edgecmd cancel historyrecoveries-cid <componentId> -id <historyRecoveryId>` | Cancel the history recovery for the specified component. | `edgecmd cancel historyrecoveries -cid Mqtt1 -id HistoryRecovery1` |
| `edgecmd resume historyrecoveries -cid <componentId> -id <historyRecoveryId>` | Resume a failed history recovery. | `edgecmd resume historyrecoveries -cid Mqtt1 -id HistoryRecovery1` |

## Secrets management configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
| `edgecmd get secrets` | Returns the entire secrets configuration. |
| `edgecmd get secrets -id <secretId>` | Returns a single secret. | `edgecmd get secrets -id exampleSecret` |
| `edgecmd set secrets -file <filePath>` | Creates/Updates the entire secret configuration. | `edgecmd set secrets -file C:\Users\TestUser\Secrets\Configuration.json` |
| `edgecmd set secrets -id <secretId> -value <secretValue> [-description <description>] [-expirationDate <expirationDate>]` | Updates an existing secret or adds a single secret into the current configuration. | `edgecmd set secrets -id exampleSecret -value secretValue -description secretDescription -expirationDate 2025-06-19T00:00:00` |
| `edgecmd remove secrets [-y]` | Deletes the entire secrets configuration. |
| `edgecmd remove secrets -id <secretId> [-y]` | Deletes a single secret. | `edgemcd remove secrets -id exampleSecret` |
| `edgecmd help secrets` | Returns secrets help information. |

## Client failover configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
| `edgecmd get clientfailover` | Returns the client failover configuration. |
| `edgecmd remove clientfailover [-y]` | Deletes the entire client failover configuration. |
| `edgecmd add clientfailver [-cid System] -file <filePath>` | Creates a client failover configuration. Fails if the client failover configuration already exists. | `edgecmd add clientfailover -file C:\Users\TestUser\ClientFailover\Configuration.json` |
| `edgecmd set clientfailover [-cid System] -file <filePath>` | Replaces the existing client failover configuration. | `edgecmd set clientfailover -file C:\Users\TestUser\ClientFailover\Configuration.json` |
| `edgecmd help clientfailover` | Returns the help information for client failover. |