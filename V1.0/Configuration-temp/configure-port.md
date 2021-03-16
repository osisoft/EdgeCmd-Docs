---
uid: ConfigurePort1-0
---

# Configure port

Complete the following procedure to change the port on which the system is listening for REST API calls using the EdgeCmd utility.

1. Access the EdgeCmd utility through a command line tool.
2. Type the following command, replacing `<portNumber>` with the port number, and press Enter.

    ```
    edgecmd Configuration System Port port=<portNumber>
    ```

    **Example:** Set port number to 5595

    ```
    edgecmd Configuration System Port port=5595
    ```

 To verify that the port number has been changed, see [Retrieve existing system configuration](xref:RetrieveExistingConfiguration1-0#view-a-specific-facet-configuration).
