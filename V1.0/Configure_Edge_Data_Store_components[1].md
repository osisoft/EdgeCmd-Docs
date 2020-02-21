---
uid: ConfigureEdgeDataStoreComponents
---

# Configure Edge Data Store components

The EdgeCmd utility enables you to add, configure, and delete Edge Data Store components.

## View configured components

Complete the following to view the components currently configured on Edge Data Store.

1. Open command line.
2. Type the following in the command line and press Enter.

	```bash
	edgecmd Configuration System Components
	```

## Add components

Complete the following to add a new component.

1. Open command line.
2. Type the following in the command line, replacing `<componentId>` and `<componentType>` with the values that you want and press Enter.

	**Note:** Valid component types are `Modbus` and `OpcUa`. If you are trying to register a Modbus EDS adapter, use `Modbus` and if you are trying to register an OPC UA adapter, use `OpcUa`.
	
	```bash
	edgecmd Configuration System Components componentId=<componentId> componentType=<componentType>
	```

	**Example**: Modbus adapter component registration

	```bash
	edgecmd Configuration System Components componentId=Modbus1 componentType=Modbus
	```

## Configure components

The Modbus TCP EDS adapter and OPC UA EDS adapter each have three configurable facets: data source, data selection, and logging. Complete the following to configure a facet.

1. Open command line.
2. Type the following in the command line, replacing `<componentId>` and `<facetName>` with the values that you want.

	```bash
	edgecmd Configuration <componentId> <facetName>
	```
	
3. Add key=value pairs to specify which values of the facet that you want to configure are to be changed and press Enter.
	
	**Example**: Configuration of the data source facet of a Modbus adapter

	```bash
	edgecmd Configuration Modbus1 DataSource IpAddress=117.23.45.110 port=502 ConnectTimeout=15000 StreamIdPrefix="DataSource1"
	```

For detailed information on how to configure each adapter, see [OPC UA EDS adapter](xref:opcUaOverview) and [Modbus TCP EDS adapter](xref:modbusOverview).

## Delete components

Complete the following to delete components from the Edge Data Store.

1. Open command line.
2. Type the following in the command line, replacing `<componentId>` with the ID of the component that you want to delete, and press Enter.

	```bash
	edgecmd Configuration System Components id=<componentId> delete
	```

**Note:** You cannot delete the Storage component because it is required for Edge Data Store to operate.
