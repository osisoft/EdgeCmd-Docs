---
uid: ConfigureEdgeDataStoreComponent1-0
---

# Configure Edge Data Store component

Use the EdgeCmd utility to add, configure, and delete Edge Data Store components.

## View configured components

Complete the following steps to view the components currently configured on Edge Data Store.

1. Access the EdgeCmd utility through a command line tool.
2. Type the following command and press Enter.

	```bash
	edgecmd Configuration System Components
	```

## Add a component

Complete the following steps to add a Modbus TCP EDS adapter component or an OPC UA EDS adapter component.

1. Access the EdgeCmd utility through a command line tool.
2. Type the following command, replacing `<componentId>` and `<componentType>` with the values for the new component and press Enter.

	**Note:** Valid component types are `Modbus` and `OpcUa`.
	
	```bash
	edgecmd Configuration System Components componentId=<componentId> componentType=<componentType>
	```

	**Example**: Modbus adapter component registration

	```bash
	edgecmd Configuration System Components componentId=Modbus1 componentType=Modbus
	```

## Configure facets of a component

The Modbus TCP EDS adapter and OPC UA EDS adapter each have three configurable facets: data source, data selection, and logging. Complete the following steps to configure a facet for a component.

1. Access the EdgeCmd utility through a command line tool.
2. Type the following command, replacing `<componentId>` and `<facetName>` with the values that you want.

	```bash
	edgecmd Configuration <componentId> <facetName>
	```
	
3. Add key=value pairs to specify the values to change and press Enter.
	
	**Example**: Configuration of the data source facet of a Modbus adapter

	```bash
	edgecmd Configuration Modbus1 DataSource IpAddress=117.23.45.110 port=502 ConnectTimeout=15000 StreamIdPrefix="DataSource1"
	```

For detailed information on how to configure each adapter, see [OPC UA EDS adapter](https://osisoft.github.io/Edge-Data-Store-Docs/V1/OpcUa/OpcUaOverview_1-0.html) and [Modbus TCP EDS adapter](https://osisoft.github.io/Edge-Data-Store-Docs/V1/Modbus/ModbusOverview_1-0.html) in the Edge Data Store documentation.

## Delete a component

Complete the following steps to delete a component from Edge Data Store.

1. Access the EdgeCmd utility through a command line tool.
2. Type the following command, replacing `<componentId>` with the ID of the component to delete, and press Enter.

	```bash
	edgecmd Configuration System Components id=<componentId> delete
	```

**Note:** You cannot delete the Storage component because it is required for Edge Data Store to operate.
