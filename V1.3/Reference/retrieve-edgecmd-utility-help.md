---
uid: RetrieveEdgeCmdUtilityHelp1-3
---

# Retrieve EdgeCmd utility help

The EdgeCmd utility provides you with help output for any operation and from any component running within an Adapter.

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter, you need to add it in the command. For example:

```cmd
edgecmd -help -port 5591 <RestOfCommand>
```

## View application help instructions

Complete the following steps to view help instructions for the entire application:

1. Access EdgeCmd utility through the command line.
2. Run the following command:
    
    ```cmd
    edgecmd help
    ```

## View component help instructions

Complete the following steps to view help instructions for configuration of a registered component that the adapter supports:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<componentId>` with ID of the component for which you want to see help output. Then press Enter.

   ```cmd
   edgecmd help -cid <componentId>
   ```

 Under [Examples](#examples), see **Configuration help for the System component**.

  **Note:** The help output also provides examples of commands that you can run to configure the component.

## View component facet help instructions

Complete the following steps to view configuration help instructions for a specific facet within a component that the adapter supports:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<facetName>` with the facet name and `<componentId>` with the ID of the component for which you want to see help output. Then press Enter.

   ```cmd
   edgecmd help <facetName> -cid <ComponentId>
   ```

 Under [Examples](#examples), see **Configuration help for the buffering facet within the System component**.

### Examples

<details>
    <summary>Configuration help for the System component</summary>
    <pre>

    edgecmd help -cid System

    ---------------------------------------------------------------------------------------------------------
    Component System command-line facet => 'Logging'
    ---------------------------------------------------------------------------------------------------------
    LogLevel                    [Optional] Desired log level settings. Options: Trace, Debug, Information, Warning, Error, Critical, None.
    LogFileSizeLimitBytes       [Optional] Maximum size in bytes of log files that the service will create for this component. Must be no less than 1000.
    LogFileCountLimit           [Optional] Maximum number of log files that the service will create for this component. Must be a positive integer.


    ---------------------------------------------------------------------------------------------------------
    Component System command-line facet => 'HealthEndpoints'
    ---------------------------------------------------------------------------------------------------------
    Id                           [Optional] Id of existing configuration to be edited of removed.
    Endpoint                     [Required] URL of OMF destination
    UserName                     [Required group 1]  User name used for authentication to PI Web API OMF endpoint.
    Password                     [Required group 1]  Password used for authentication to PI Web API OMF endpoint.
    ClientId                     [Required group 2]  Client ID used for authentication to OSIsoft Cloud Services.
    ClientSecret                 [Required group 2]  Client Secret used for authentication to OSIsoft Cloud Services.
    TokenEndpoint                [Optional group 2] URL of OMF destination's token service.
    ValidateEndpointCertificate  [Optional] If true, endpoint certificate will be validated (recommended). If false, any endpoint certificate will be accepted. OSIsoft strongly recommends using disabled endpoint certificate validation for testing purposes only.

    Note: Only one Required group must be specified. Group 1 for PI Web API or Group 2 for OCS.


    ---------------------------------------------------------------------------------------------------------
    Component System command-line facet => 'Components'
    ---------------------------------------------------------------------------------------------------------
    ComponentId                    [Required] ID of the hosted component.
    ComponentType                  [Required] Type of the hosted component. Valid component types: OmfEgress, OpcUa.


    ---------------------------------------------------------------------------------------------------------
    Component System command-line facet => 'Buffering'
    ---------------------------------------------------------------------------------------------------------
    BufferLocation                 [Required] Location of the on-disk buffers.
    MaxBufferSizeMB                [Optional] Maximum size of the on-disk or in-memory buffers.
    EnablePersistentBuffering      [Optional] Enable or disable on-disk buffering.


    ---------------------------------------------------------------------------------------------------------
    Component System command-line facet => 'General'
    ---------------------------------------------------------------------------------------------------------
    EnableDiagnostics              [Optional] Enable application diagnostics.
    MetadataLevel                  [Optional] Defines amount of metadata sent to OMF endpoints. Options: None, Low, Medium, High.

  </pre>
  </details>

  <details>
      <summary>Configuration help for the Buffering facet within the System component</summary>
      <pre>

      edgecmd help Buffering -cid System

      ---------------------------------------------------------------------------------------------------------
      Component System command-line facet => 'Buffering'
      ---------------------------------------------------------------------------------------------------------
      BufferLocation                 [Required] Location of the on-disk buffers.
      MaxBufferSizeMB                [Optional] Maximum size of the on-disk or in-memory buffers.
      EnablePersistentBuffering      [Optional] Enable or disable on-disk buffering.

 </pre>
</details>
