---
uid: RetrieveEdgeCmdUtilityHelp
---

# Retrieve EdgeCmd utility help

The EdgeCmd utility includes command-line syntax help that can be accessed directly from a command line. 

## View general help

Complete the following steps to view help on how to use the Edgecmd utility:

1. Open a command prompt.
2. Type the following command and press Enter.

	```bash
	edgecmd Help
	```

## View component help

Complete the following steps to view help for a registered component for Edge Data Store:

1. Open a command prompt.
2. Type the following command, replacing `<componentId>` with the component ID, and press Enter.

	```bash
	edgecmd Help <componentId>
	```

	For more information, see the example, [Help for the System component](#help-for-the-system-component).
	
	**Note:** The help includes examples of commands used to configure the component.
	
	
## View component facet help

Complete the following steps to view help for a specific facet within a component:

1. Open a command prompt.
2. Type the following command, replacing `<componentId>` and `<facetName>` with the component ID and the facet name, and press Enter.

	```bash
	edgecmd Help <componentId> <facetName>
	```
	
	For more information, see the example, [Help for the Port facet within the System component](#help-for-the-port-facet-within-the-system-component).

### Examples

#### Help for the System component:

```bash
edgecmd Help System

---------------------------------------------------------------------------------------------------------
Component System command-line options => 'Logging'
---------------------------------------------------------------------------------------------------------
LogLevel                    [Required] Desired log level settings. Options: Verbose, Information, Warning, Error, Fatal.
LogFileSizeLimitBytes       [Required] Maximum size in bytes of log files that the service will create for this component. Must be no less than 1000.
LogFileCountLimit           [Required] Maximum number of log files that the service will create for this component. Must be a positive integer.

Example: ./edgecmd Configuration System Logging LogLevel=Warning
Example: ./edgecmd Configuration System Logging LogFileSizeLimitBytes=32768
Example: ./edgecmd Configuration System Logging LogFileCountLimit=5


---------------------------------------------------------------------------------------------------------
Component System command-line options => 'HealthEndpoints'
---------------------------------------------------------------------------------------------------------
Id                           [Optional] Id of existing configuration to be edited of removed.
Endpoint                     [Required] URL of OMF destination
UserName                     [Required group 1]  User name used for authentication to PI Web API OMF endpoint.
Password                     [Required group 1]  Password used for authentication to PI Web API OMF endpoint.
ClientId                     [Required group 2]  Client ID used for authentication to OSIsoft Cloud Services.
ClientSecret                 [Required group 2]  Client Secret used for authentication to OSIsoft Cloud Services.
Buffering                    [Optional] Set the buffering type for messages to this endpoint. Options are 'memory', 'disk' or 'none'. Defaults to 'none'.
MaxBufferSizeMB              [Optional] If an integer >0, this is the limit on the maximum megabytes of data to buffer for messages to this endpoint. Useful for limiting memory or disk usage growth in the event of disconnection to the endpoint. If the buffer is full, old messages will be discarded for new messages. Defaults to 0.
ValidateEndpointCertificate  [Optional] If true, endpoint certificate will be validated (recommended). If false, any endpoint certificate will be accepted. OSIsoft strongly recommends using disabled endpoint certificate validation for testing purposes only.

Note: Only one Required group must be specified. Group 1 for PI Web API or Group 2 for OCS.
Example: ./edgecmd Configuration System HealthEndpoints Endpoint=endpointURL UserName=UserName Password=Password


---------------------------------------------------------------------------------------------------------
Component System command-line options => 'Port'
---------------------------------------------------------------------------------------------------------
Port                        [Required] The TCP port to bind this application host to (Range [1024,65535])

Example: ./edgecmd Configuration System Port Port=5590


---------------------------------------------------------------------------------------------------------
Component System command-line options => 'Components'
---------------------------------------------------------------------------------------------------------
ComponentId                        [Required] ID of the hosted component.
ComponentType                      [Required] Type of the hosted component.

Example: ./edgecmd Configuration System Components ComponentId=Modus1 ComponentType=Modbus
```

#### Help for the Port facet within the System component

```bash
edgecmd Help System Port

---------------------------------------------------------------------------------------------------------
Component System command-line options => 'Port'
---------------------------------------------------------------------------------------------------------
Port                        [Required] The TCP port to bind this application host to (Range [1024,65535])

Example: ./edgecmd Configuration System Port Port=5590
```
