---
uid: RetrieveExistingConfiguration1-0
---

# Retrieve existing configuration

Use the EdgeCmd utility to view the configuration for the components of Edge Data Store.

## View all components configuration

Complete the following steps to view the configuration of every component in Edge Data Store:

1. Access the EdgeCmd utility through a command line tool.
2. Type the following command and press Enter.

   ```bash
   edgecmd Configuration
   ```
  
  
## View a specific component configuration

Complete the following steps to view the configuration of a specific component:

1. Access the EdgeCmd utility through a command line tool.
2. Type the following command, replacing `<componentId>` with the ID of the component, and press Enter.

   ```bash
   edgecmd Configuration <componentId>
   ```
   
   For more information, see the example, [View the configuration of the System component](#view-the-configuration-of-the-system-component).

## View a specific facet configuration

Complete the following steps to view the configuration of a specific facet of a component:

1. Access the EdgeCmd utility through a command line tool.
2. Type the following command, replacing `<componentId>` and `<facetName>` with the ID of the component and the facet name, and press Enter.

   ```bash
   edgecmd Configuration <componentId> <facetName>
   ```
   For more information, see the example, [View the configuration of the Logging facet within the Storage component](#view-the-configuration-of-the-logging-facet-within-the-storage-component).
   
## View a specific facet entry configuration

Complete the following steps to view the configuration of a specific facet entry of a component:

1. Access the EdgeCmd utility through a command line tool.
2. Type the following command, replacing `<componentId>` and `<facetName>` with the ID of the component and the facet name.

   ```bash
   edgecmd Configuration <componentId> <facetName> id=IndexToRetrieve
   ```

3. Add the key=value pairs for the facet to configure, for example `id=IndexToRetrieve`, and press Enter.

   For more information, see the example, [View the configuration of a specific entry in the PeriodicEgressEndpoint facet within the Storage component](#view-the-configuration-of-a-specific-entry-in-the-periodicegressendpoint-facet-within-the-storage-component).

### Examples

#### View the configuration of the System component

```bash
edgecmd Configuration System
{
  "Logging": {
    "logLevel": "Information",
    "logFileSizeLimitBytes": 34636833,
    "logFileCountLimit": 31
  },
  "HealthEndpoints": [],
  "Port": {
    "port": 5590
  },
  "Components": [
    {
      "componentId": "Storage",
      "componentType": "EDS.Component"
    }
  ]
}
```

#### View the configuration of the Logging facet within the Storage component

```bash
edgecmd Configuration Storage Logging
{
  "logLevel": "Information",
  "logFileSizeLimitBytes": 34636833,
  "logFileCountLimit": 31
}
```

#### View the configuration of a specific entry in the PeriodicEgressEndpoint facet within the Storage component

```bash
edgecmd Configuration Storage PeriodicEgressEndpoints id=Endpoint_1
{
  "id": "Endpoint_1",
  "executionPeriod": "2.00:00:00",
  "name": null,
  "description": null,
  "enabled": true,
  "endpoint": "http://localhost:5590",
  "clientId": null,
  "clientSecret": null,
  "userName": "user_54",
  "password": "***************",
  "validateEndpointCertificate": true,
  "tokenEndpoint": null,
  "debugExpiration": null,
  "namespaceId": "default",
  "backfill": false,
  "egressFilter": null,
  "streamPrefix": null,
  "typePrefix": null
}
```
