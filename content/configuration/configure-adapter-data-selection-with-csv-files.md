---
uid: ConfigureAdapterDataSelectionWithCSVFiles
---

# Configure adapter data selection with .csv files

Use EdgeCmd utility to import data selection from, and export it into, a .csv (comma-separated value) file.

EdgeCmd utility recognizes the content in .csv format from the specified file path and converts it.

**Note:** The .csv file needs to include a header row.

## Import data selection from a .csv file

Complete the following steps to import data selection from a .csv file

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<componentId>` with the ID of the component and `<PathToCsvFile>` with the path to the .csv file from which you want to import the data selection. Then press Enter.

    ```cmd
    edgecmd set DataSelection -cid <componentId> -file <PathToCsvFile> -csv
    ```

## Export data selection into a .csv file

Complete the following steps to export data selection into a .csv file

1. Access EdgeCmd utility through the command line.
2. Type the following in the command line, replacing `<componentId>` with the ID of the component for which you want to export the data selection. Then press Enter.

    ```cmd
    edgecmd get DataSelection -cid <componentId> [-file <PathToCsvFile>] -csv
    ```

    If you omit the optional parameter and its argument `-file` `PathToCsvFile`, the contents are written to the standard output terminal or console.

    <details>
    <summary>Sample output</summary>
    <pre>

        edgecmd get DataSelection -cid OpcUa1 -csv

        selected,name,nodeId,streamId,dataFilterId
        True,Counter,ns=3;s=Counter,3.Counter,
        True,ByteAnalogItem,ns=6;s=ByteAnalogItem,6.ByteAnalogItem,
        True,DoubleAnalogItem,ns=6;s=DoubleAnalogItem,6.DoubleAnalogItem,
        True,FloatAnalogItem,ns=6;s=FloatAnalogItem,6.FloatAnalogItem,
        True,Int16AnalogItem,ns=6;s=Int16AnalogItem,6.Int16AnalogItem,
        True,Int32AnalogItem,ns=6;s=Int32AnalogItem,6.Int32AnalogItem,
        True,Int64AnalogItem,ns=6;s=Int64AnalogItem,6.Int64AnalogItem,
        True,SByteAnalogItem,ns=6;s=SByteAnalogItem,6.SByteAnalogItem,
        True,UInt16AnalogItem,ns=6;s=UInt16AnalogItem,6.UInt16AnalogItem,
        True,UInt32AnalogItem,ns=6;s=UInt32AnalogItem,6.UInt32AnalogItem,
        True,UInt64AnalogItem,ns=6;s=UInt64AnalogItem,6.UInt64AnalogItem,
        True,BooleanDataItem,ns=6;s=BooleanDataItem,6.BooleanDataItem,
        True,ByteDataItem,ns=6;s=ByteDataItem,6.ByteDataItem,
        True,DateTimeDataItem,ns=6;s=DateTimeDataItem,6.DateTimeDataItem,
        True,DoubleDataItem,ns=6;s=DoubleDataItem,6.DoubleDataItem,
        True,FloatDataItem,ns=6;s=FloatDataItem,6.FloatDataItem,
        True,Int16DataItem,ns=6;s=Int16DataItem,6.Int16DataItem,
        True,Int32DataItem,ns=6;s=Int32DataItem,6.Int32DataItem,
        True,Int64DataItem,ns=6;s=Int64DataItem,6.Int64DataItem,
        True,SByteDataItem,ns=6;s=SByteDataItem,6.SByteDataItem,
        True,StringDataItem,ns=6;s=StringDataItem,6.StringDataItem,
        True,UInt16DataItem,ns=6;s=UInt16DataItem,6.UInt16DataItem,
        True,UInt32DataItem,ns=6;s=UInt32DataItem,6.UInt32DataItem,
        True,UInt64DataItem,ns=6;s=UInt64DataItem,6.UInt64DataItem,

    </pre>
    </details>

**Note:** EdgeCmd utility translates `null` values into an empty string for the `get` operation, while it interprets empty strings as `null` values for the `set` operation. To specify an empty string for the configuration, use double quotes `""`.
