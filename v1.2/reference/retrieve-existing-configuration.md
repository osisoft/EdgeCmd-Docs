---
uid: RetrieveExistingConfiguration1-2
---

# Retrieve existing configuration

Use EdgeCmd utility to view the configuration for each part of the adapter.

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter, you need to add it in the command. For example:

```cmd
edgecmd -port=5591 Configuration <RestOfTheCommand>
```

## View adapter configuration

Complete the following steps to view the configuration for the adapter:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line and then press Enter.

   ```cmd
   edgecmd get application
   ```

   Under [Examples](#examples), see **View the configuration of the adapter**.
  
## View configured components

Complete the following steps to view the components currently configured on the adapter:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line and then press Enter.

   ```cmd
   edgecmd get components
   ```
  
## View a specific component configuration

Complete the following steps to view the configuration of a specific component:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<componentId>` with the ID of the component for which you want to see the configuration. Then press Enter.

   ```cmd
   edgecmd get -cid <componentId>
   ```

   Under [Examples](#examples), see **View the configuration of the System component**.

## View a specific facet configuration

Complete the following steps to view the configuration of a specific facet of an adapter component:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<facetName>` with the name of the facet, and `<componentId>` with the ID of the component for which you want to see the configuration. Then press Enter.

   ```cmd
   edgecmd get <facetName> -cid  <componentId>
   ```
  
   Under [Examples](#examples), see **View the configuration of the Logging facet within the OmfEgress component**.
  
## View a specific facet entry configuration

Complete the following steps to view the configuration of a specific facet entry of a component:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<facetName>` with the name of the facet, `<componentId>` with the ID of the component and `<index>` with the name of the facet entry for which you want to see the configuration.

   ```cmd
   edgecmd get <facetName> -cid <componentId> -id <index>
   ```

   Under [Examples](#examples), see **View the configuration of a specific entry in the HealthEndpoints facet within the System component**.

### Examples

<details>
    <summary>View the configuration of the adapter</summary>
    <pre>

      edgecmd get application
      
      {
        "OmfEgress": {
          "Logging": {
            "logLevel": "Information",
            "logFileSizeLimitBytes": 34636833,
            "logFileCountLimit": 31
          },
          "DataEndpoints": []
        },
        "System": {
          "Logging": {
            "logLevel": "Information",
            "logFileSizeLimitBytes": 34636833,
            "logFileCountLimit": 31
          },
          "HealthEndpoints": [],
          "Components": [
            {
              "componentId": "OmfEgress",
              "componentType": "OmfEgress"
            },
            {
              "componentId": "OpcUa1",
              "componentType": "OpcUa"
            }
          ],
          "Buffering": {
            "bufferLocation": "C:/ProgramData/OSIsoft/Adapters/OpcUa/Buffers",
            "maxBufferSizeMB": 1024,
            "enablePersistentBuffering": true
          },
          "General": {
            "enableDiagnostics": true,
            "metadataLevel": "Medium"
          }
        },
        "OpcUa1": {
          "Logging": {
            "logLevel": "Information",
            "logFileSizeLimitBytes": 34636833,
            "logFileCountLimit": 31
          },
          "DataSource": {},
          "DataFilters": [
            {
              "id": "DuplicateData",
              "absoluteDeadband": 0,
              "percentChange": null,
              "expirationPeriod": "1:00:00"
            }
          ],
          "DataSelection": [],
          "ClientSettings": {}
        }
      }

 </pre>
</details>

<details>
    <summary>View the configuration of the System component</summary>
    <pre>

    edgecmd get component System
    {
      "Logging": {
        "logLevel": "Information",
        "logFileSizeLimitBytes": 34636833,
        "logFileCountLimit": 31
    },
    "HealthEndpoints": [],
    "Components": [
      {
        "componentId": "OmfEgress",
        "componentType": "OmfEgress"
      },
      {
        "componentId": "OpcUa1",
        "componentType": "OpcUa"
      }
    ],
    "Buffering": {
      "bufferLocation": "C:/ProgramData/OSIsoft/Adapters/OpcUa/Buffers",
      "maxBufferSizeMB": 1024,
      "enablePersistentBuffering": true
    },
    "General": {
      "enableDiagnostics": true,
      "metadataLevel": "Medium"
    }
  }

 </pre>
</details>

<details>
    <summary>View the configuration of the Logging facet within the OmfEgress component</summary>
    <pre>

      edgecmd get Logging -cid OmfEgress
      {
        "logLevel": "Information",
        "logFileSizeLimitBytes": 34636833,
        "logFileCountLimit": 31
      }

 </pre>
</details>

<details>
    <summary>View the configuration of a specific entry in the HealthEndpoints facet within the System component</summary>
    <pre>

      edgecmd get HealthEndpoints -cid System -id PWA
      {
        "id": "PWA",
        "endpoint": "https://localhost:5821/piwebapi/omf",
        "userName": "user-54",
        "password": "***************",
        "clientId": null,
        "clientSecret": null,
        "tokenEndpoint": null,
        "validateEndpointCertificate": true
      }

 </pre>
</details>
