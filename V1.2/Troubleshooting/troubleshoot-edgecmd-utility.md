---
uid: TroubleShootEdgeCmdUtility1-2
---

# Troubleshoot EdgeCmd utility

To troubleshoot issues with EdgeCmd utility, you can start with the following troubleshooting tips. If you are unable to resolve issues with EdgeCmd utility or need additional guidance, contact OSIsoft Technical Support.

1. To get more information on proper usage of EdgeCmd utility, use the `help` command on a particular command and facet.<br>For more information, see [Retrieve EdgeCmd utility help](xref:RetrieveEdgeCmdUtilityHelp1-2).
2. Check if your adapter is using the default port number `5590`.

    - If the adapter is using any other port number, include `-port <AdapterPortNumber>` as an argument in your command.
    - If you do not know what port to use, check the `appsettings.json` file in the directory where the adapter is installed. 

3. Check if the adapter is running.<br>EdgeCmd utility makes REST calls against an active adapter. If the adapter is not running, there is nothing to respond to those REST requests.
4. If you run a command like `Reset`, add a data source configuration, or edit a large data selection, and so on. Wait 20 to 60 seconds before you attempt to make more calls; the adapter needs time to process the request.
5. If a command is not working in EdgeCmd utility, verify the command does not work in other REST clients like Postman either.
