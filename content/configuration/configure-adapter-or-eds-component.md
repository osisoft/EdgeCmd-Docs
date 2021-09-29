---
uid: ConfigureAdapterOrEDSComponent
---

# Configure adapter or EDS component

Use EdgeCmd utility to add and remove adapter or EDS components, and to configure facets of the components.

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter or EDS, you need to add it in the command. For example:

```cmd
edgecmd -port 5591 <RestOfTheCommand>
```

**Note:** If a command contains slashes, you must add escape characters as follows:<br> 
  - In *Windows*, add a second slash.<br> 
       Example: `TestUser\OilCompany` becomes `TestUser\\OilCompany`
       
  - In *Linux*, add three additional slashes.<br>
       Example: `TestUser\OilCompany` becomes `TestUser\\\\OilCompany`

## Add components

Complete the following steps to add a new component:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<componentType>` and `<componentId>` with the values for the component and press Enter.

    **Note:** The only valid component type is the adapter or EDS type. For example, if you are trying to register a new Modbus component, use `Modbus` and if you are trying to register an OPC UA component, use `OpcUa`. Refer to the specific adapter or EDS user guide for the component type.

    ```cmd
    edgecmd add Components [-type <componentType>] [-id <componentId>]
    ```

    **Example**: Modbus adapter component registration

    ```cmd
    edgecmd add Components -type Modbus -id Modbus1
    ```

## Configure a facet of a component

All adapters and EDS have different configurable facets. Complete the following steps to configure a facet:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<facetName>` and `<componentId>` with their respective values. Then press Enter.

    ```cmd
    edgecmd set <facetName> -cid <componentId> [-file <filepath>]
    ```

    **Example**: Configuration of the data source facet of a Modbus adapter

    ```cmd
    edgecmd set DataSource -cid Modbus1 -file C:\Users\TestUser\Modbus1\DataSource.json
    ```

    **Note:** For more information on adapter or EDS specific facets, see the respective adapter or EDS documentation.

## Remove a component

Complete the following steps to remove a component from the adapter or EDS:

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<componentId>` with the ID of the component to remove, and press Enter. Edgecmd will prompt with "Please Confirm [y/N]: " unless you include the optional *-y* parameter.

    ```cmd
    edgecmd remove Components [-id <componentId] [-y]
    ```

    **Example**: Removal of the Modbus component

    ```cmd
    edgecmd remove Components -id Modbus1
    ```

**Note:** You cannot remove the OmfEgress from PI adapters or the Storage component from EDS. They are required for the products to operate.
