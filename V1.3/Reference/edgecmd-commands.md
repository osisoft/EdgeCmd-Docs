---
uid: EdgeCmdCommands1-3
---

# EdgeCmd commands

The following tables provide a description of every command available in EdgeCmd utility. Every command used with the EdgeCmd utility has to be preceded by `edgecmd`. Parts of the command that are in `[ ]` are optional and do not need to be specified.

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
`edgecmd help [<target>]` | Display configuration help output for System level targets, for example `application`, `healthendpoints`, and `logging`. | `edgecmd help System`
`edgecmd  help <target> -cid <componentId>` | Display configuration help output for any registered component and facet.  | `edgecmd help DataSource -cid opcua1` 
`edgecmd help -cid <componentId>` | Display configuration help output for any registered component. | `edgecmd help -cid OpcUa1`

## Port configuration

EdgeCmd command| Description | Example |
---------------|-------------|----------|
`edgecmd -port 5590 <command> [-cid <componentId>]` | Specify the port number for communication with EDS or the adapter. | `edgecmd -port 5595 get Components`
`edgecmd -port 5590 <command> [-cid <componentId>] -port <port>` | Specify the port number for the adapter or EDS payload. | `edgecmd -port 5590 edit datasource -cid Mqtt1 -port 1885`

For more information on how to configure a payload port number, see [Configure an adapter or EDS with commands](xref:ConfigureAnAdapterOrEDSWithCommands#configure-payload-port).

## Application configuration

The following commands configure the application.

EdgeCmd command| Description | Example |
---------------|-------------|----------|
`edgecmd get Application [-file <filepath>]` | Get the configuration for every platform component. | `edgecmd get Application`
`edgecmd set Application -file <filepath>` | Import the entire configuration for a PI adapter or EDS. | `edgecmd set Application -file C:\Users\TestUser\Adapter\Configuration.json`
`edgecmd reset Application`  | Reset the entire application and storage in EDS. |
`edgecmd help Application` | Display help output for the application target.

## System component configuration

The following commands configure specific facets of the system component.

### Components facet configuration

EdgeCmd command| Description | Example |
---------------|-------------|----------|
`edgecmd get Components [-file <filepath>]` | Get the component configuration. | `edgecmd get Components`
`edgecmd set Components [-file <filepath>]` | Import components configuration. | `edgecmd set Components -file C:\Users\TestUser\Components\Configuration.json`
`edgecmd add Components [-type <type>] [-id <componentId>]`  | Add component to components configuration. | `edgecmd add Components  -type Modbus -id Modbus1`
`edgecmd remove Components [-id <componentId] [-y]` | Remove specified component from configuration. | `edgecmd remove Components -id Modbus1`
`edgecmd help Components`| Display help output for components configuration. |

### Buffering facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get Buffering [-file <filepath>]` | Get the buffering configuration. | `edgecmd get Buffering C:\Users\TestUser\Buffering\Configuration.json`
`edgecmd set Buffering [-file <filepath>]` | Import buffering configuration. | `edgecmd set Buffering`
`edgecmd edit Buffering [-bufferLocation <value>] [-maxBufferSizeMB <value>] [-enableBuffering <value>]`  | Change buffering configuration. | `edgecmd Buffering -bufferLocation C:/ProgramData/OSIsoft/Adapters/Modbus/Buffers -maxBufferSizeMB 1024 -enableBuffering true`
`edgecmd help Buffering` | Display help output for buffering configuration.

### Health endpoints facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get HealthEndpoints [-file <filepath>]` | Get the health endpoints configuration. | `edgecmd get HealthEndpoints`
`edgecmd set HealthEndpoints [-file <filepath>]` | Import health endpoints configuration. | `edgecmd set HealthEndpoints -file C:\Users\TestUser\HealthEndpoints\Configuration.json`
`edgecmd add HealthEndpoints [-id <string>] [-Endpoint <endpointUrl>] [-UserName <userName>] [-Password <password>] [-ClientId <clientId>] [-ClientSecret <clientSecret>] [-TokenEndpoint <tokenEndpoint>] [-ValidateEndpointCertificate <true/false>]`  | Add a health endpoint. | `edgecmd add HealthEndpoints -id OCS -Endpoint https://OCS_OMF_endpoint -ClientId TestUser -ClientSecret TestPassword`
`edgecmd edit HealthEndpoints [-id <string>] [-Endpoint <endpointUrl>] [-UserName <userName>] [-Password <password>] [-ClientId <clientId>] [-ClientSecret <clientSecret>] [-TokenEndpoint <tokenEndpoint>] [-ValidateEndpointCertificate <true/false>]` | Change a health endpoint. | `edgecmd edit HealthEndpoints -id OCS -Endpoint https://OCS_OMF_endpoint -ClientId TestUser -ClientSecret TestPassword`
`edgecmd remove HealthEndpoints [-id <string>] [-y]`| Remove health endpoint. | `edgecmd remove HealthEndpoints -id OCS`
`edgecmd help HealthEndpoints` | Display help output for health endpoints configuration.

## OMF egress data endpoints facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get DataEndpoints [-file <filepath>]` | Get the data endpoints configuration. | `edgecmd get DataEndpoints`
`edgecmd set DataEndpoints [-file <filepath>]` | Import data endpoints configuration. | `edgecmd set DataEndpoints -file C:\Users\TestUser\DataEndpoints\Configuration.json`
`edgecmd add DataEndpoints [-id <endpointId>] [-Endpoint <endpointUrl>] [-UserName <userName>] [-Password <password>] [-ClientId <clientId>] [-ClientSecret <clientSecret>] [-TokenEndpoint <tokenEndpoint>] [-ValidateEndpointCertificate <true/false>]`  | Add data endpoints. | `edgecmd add DataEndpoints -id PI Web Api  -Endpoint https://pi_web_api_server/piwebapi/omf/ -UserName TestUser -Password TestPassword -ValidateEndpointCertificate false`
`edgecmd edit DataEndpoints -id <string> [-Endpoint <endpointUrl>] [-UserName <userName>] [-Password <password>] [-ClientId <clientId>] [-ClientSecret <clientSecret>] [-TokenEndpoint <tokenEndpoint>] [-ValidateEndpointCertificate <true/false>]` | Change a data endpoint. | `edgecmd edit DataEndpoints -id PI Web Api -Endpoint https://pi_web_api_server/piwebapi/omf/ -UserName TestUser -Password TestPassword -ValidateEndpointCertificate true` |
`edgecmd remove DataEndpoints -id <string> [-y]`| Remove specified data endpoint. | `edgecmd remove DataEndpoints -id PI Web API`
`edgecmd remove DataEndpoints [-y]`| Remove all data endpoints. | `edgecmd remove DataEndpoints -y`
`edgecmd help DataEndpoints`| Display help output for data endpoints configuration.

## Component

The following commands configure a component.

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get -cid <componentId> [-file <filepath>]` | Get the configuration of specified component. | `edgecmd get -cid OpcUa1`
`edgecmd set -cid <componentId> -file <filepath>` | Import configuration for a component. | `edgecmd set -cid Modbus1 -file C:\Users\TestUser\Components\Configuration.json`
`edgecmd remove -cid <componentId> [-y]`  | Remove specified component. | `edgecmd remove -cid OpcUa1 -y`
`edgecmd start -cid <componentId>` | Start specified component. | `edgecmd start -cid Modbus1`
`edgecmd stop -cid <componentId>`| Stop specified component. | `edgecmd stop -cid OpcUa1`
`edgecmd help -cid <componentId>` | Display help output for specified component. | `edgecmd help -cid Modbus1`

The following commands configure specific facets of a component.

### Logging facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get Logging [-cid <componentId>] [-file <filepath>]` | Get the logging configuration for specified component. | `edgecmd get Logging -cid Modbus1`
`edgecmd set Logging [-cid <componentId>] [-file <filepath>]` | Import logging configuration of specified component. | `edgecmd set Logging -cid OpcUa1`
`edgecmd edit Logging [-cid <componentId>] [-LogLevel <logLevel>] [-LogFileSizeLimitBytes <MaxSize>] [-LogFileCountLimit <FileCount>]`  | Change logging configuration for specified component | `edgecmd edit Logging -cid Modbus1 -LogLevel Information -LogFileSizeLimitBytes 4567 -LogFileCountLimit 123`
`edgecmd help Logging` | Display help output for logging facet |

### Schedules facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get Schedules -cid <componentId> [-file <filepath>]` | Get the schedules configuration for specified component. | `edgecmd get Schedules -cid Modbus1`
`edgecmd set Schedules -cid <componentId> [-file <filepath>]` | Import schedules configuration for specified component. | `edgecmd set Schedules -cid OpcUa1 -file C:\Users\TestUsers\Schedules\Configuration.json`
`edgecmd add Schedules -cid <componentId> -id <itemid> [-Period <period>] [-Offset <offset>]`  | Add schedules configuration for specified component. | `edgecmd add Schedules -cid Modbus1 -id Schedule1 -Period 125 -Offset 25`
`edgecmd edit Schedule -cid <componentId> -id <itemid> [-Period <period>] [-Offset <offset>]` | Change schedules configuration for specified component. | `edgecmd edit Schedule -cid OpcUa1 -id Schedule2`
`edgecmd remove Schedule -cid <componentId> [-id <itemid>] [-y]`| Remove schedules configuration for item in specified component. | `edgecmd remove Schedule -cid Modbus1 -id Schedule3 -y`
`edgecmd remove Schedule -cid <componentId> [-y]` | Remove schedules configuration for specified component. | `edgecmd remove Schedule -cid OpcUa1`
`edgecmd help Schedule –cid <componentId>`| Display help output for schedules facet. | `edgecmd help Schedule -cid Modbus1`

### Data filters facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get DataFilters -cid <componentId> [-file <filepath>]` | Get the data filters configuration for specified component. | `edgecmd get DataFilters -cid OpcUa1`
`edgecmd set DataFilters -cid <componentId> [-file <filepath>]` | Import data filters configuration for specified component. | `edgecmd set DataFilters -cid Modbus1 -file C:\Users\TestUser\DataFilters\Configuration.json`
`edgecmd add DataFilters -cid <componentId> -id <itemid> [-AbsoluteDeadband <value>] [-PercentChange <value>] [-ExpirationPeriod <value>]`  | Add data filters configuration for specified component. | `edgecmd add DataFilters -cid OpcUa1 -id DuplicateData -AbsoluteDeadband 0 -PercentChange 35`
`edgecmd edit DataFilters -cid <componentId> -id <itemid> [-AbsoluteDeadband <value>] [-PercentChange <value>] [-ExpirationPeriod <value>]` | Change data filters configuration for specified component. | `edgecmd edit DataFilters -cid Modbus1 -id DuplicateData -AbsoluteDeadband 3 -PercentChange 35`
`edgecmd remove DataFilters -cid <componentId> [-id <itemid>] [-y]`| Remove data filters configuration for item in specified component. | `edgecmd remove DataFilters -cid OpcUa1 -y`
`edgecmd help DataFilters –cid <componentId>` | Display help output for data filters facet. | `edgecmd help DataFilters -cid Modbus1`

### Data source facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get DataSource -cid <componentId>` | Get the data source configuration for specified component. | `edgecmd get DataSource -cid OpcUa1`
`edgecmd set DataSource -cid <componentId> [-file <filepath>]` | Import data source configuration for specified component. | `edgecmd set DataSource -cid Modbus1 -file C:\Users\TestUser\DataSource\Configuration.json`
`edgecmd set DataSource -cid <componentId> [-<adapterSpecificParameter> <value>]`  | Import data source configuration parameter for specified component. | `edgecmd set DataSource -cid OpcUa1 -UseSecureConnection true`
`edgecmd edit DataSource -cid <componentId> [-<adapterSpecificParameter> <value>]` | Change data source configuration parameter for specified component. | `edgecmd edit DataSource -cid Modbus1 -UseSecureConnection false`
`edgecmd remove Datasource -cid <componentId> [-y]`| Remove data source configuration for specified component. | `edgecmd remove Datasource -cid OpcUa1 -y`
`edgecmd help Datasource -cid <componentId>` | Display help output for data source facet. | `edgecmd help Datasource -cid Modbus1`

### Data selection facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get DataSelection -cid <componentId> [-file <filepath>]` | Get the data selection configuration for specified component. | `edgecmd get DataSelection -cid Modbus1 -file C:\Users\TestUser\DataSelection\Configuration.json`
`edgecmd set DataSelection -cid <componentId> [-file <filepath>]` | Import data selection configuration for specified component. | `edgecmd set DataSelection -cid OpcUa1`
`edgecmd get DataSelection -cid <componentId> [-file <filepath>] -csv` | Display data selection configuration for specified component in CSV format. | `edgecmd get DataSelection -cid Modbus1 -file C:\Users\TestUser\DataSelection\Configuration.csv -csv`
`edgecmd set DataSelection -cid <componentId> [-file <filepath>] -csv` | Import data selection configuration for specified component in CSV format. | `edgecmd set DataSelection -cid OpcUa1 -csv`
`edgecmd add  DataSelection -cid <componentId> -id <itemid>] [-<adapterSpecificParameter> <value>]`  | Add data selection configuration for specified component. | `edgecmd add DataSelection -cid OpcUa1 -id Custom1 -Name RandomName`
`edgecmd edit DataSelection -cid <componentId> [-id <itemid>] [-<adapterSpecificParameter> <value>]` | Change data selection configuration for specified component. | `edgecmd edit DataSelection -cid Modbus1 -Selected true`
`edgecmd remove  DataSelection -cid <componentId> [-id <itemid>] [-y]`| Remove data selection configuration for item in specified component. | `edgecmd remove DataSelection -cid OpcUa1 -id Random1`
`edgecmd remove DataSelection -cid <componentId> [-y]` | Remove data selection configuration for specified component. | `edgecmd remove DataSelection -cid Modbus1 -y`
`edgecmd help DataSelection -cid <componentId>`| Display help output for data selection facet. | `edgecmd help DataSelection -cid OpcUa1`

### General facet configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get <FacetName> -cid <componentId> [-file <filepath>]` | Get the configuration for specified facet in specified component. | `edgecmd get Logging -cid Modbus1`
`edgecmd set <FacetName> -cid <componentId> [-file <filepath>]` | Import configuration for specified facet in specified component. | `edgecmd set DataFilters -cid OpcUa1`
`edgecmd add <FacetName> -cid <componentId> [-<facetSpecificParameter> <value>]`  | Add configuration for specified facet in specified component. | `edgecmd add Logging -cid Modbus1 -LogFileCountLimit 30`
`edgecmd edit <FacetName> -cid <componentId> [-<facetSpecificParameter> <value>]` | Change configuration for specified facet in specified component. | `edgecmd edit DataFilters -cid OpcUa1 -AbsoluteDeadband 0`
`edgecmd remove <FacetName> -cid <componentId> [-y]`| Remove configuration for specified facet in specified component. | `edgecmd remove Logging -cid Modbus1 -y`
`edgecmd help <FacetName> -cid <componentId>` | Display help out output for specified facet in specified component. | `edgecmd help DataFilters -cid OpcUa1`

## EDS configuration

### Storage configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get Storage` | Get the Storage configuration. |
`edgecmd set Storage [-file <string>]` | Import Storage configuration. | `edgecmd set Storage -file C:\Users\TestUser\Storage\Configuration.json`
`edgecmd reset Storage [-y]` | Reset Storage configuration. | `edgecmd reset Storage -y`
`edgecmd help Storage`| Display help output for Storage configuration. |

### Runtime configuration

EdgeCmd command| Description | Examples |
---------------|-------------|----------|
`edgecmd get Runtime` | Get the runtime configuration. |
`edgecmd set Runtime [-file <filepath>]` | Import runtime configuration. | `edgecmd set Runtime -file C:\Users\TestUser\Runtime\Configuration.json`
`edgecmd edit Runtime [-parameter <value>]`  | Change runtime configuration. | `edgecmd edit Runtime`
`edgecmd help Runtime` | Display help output for runtime configuration.

## Diagnostics configuration

EdgeCmd command| Description |
---------------|-------------|
`edgecmd get Diagnostics` | Get the diagnostics configuration. |
`edgecmd get Version` | Get version information.
