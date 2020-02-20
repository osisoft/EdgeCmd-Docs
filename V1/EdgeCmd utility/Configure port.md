---
uid: ConfigurePort
---

# Configure port

Complete the following procedure to configure or change the port on which the system is listening for REST API calls.

1. Open command line.
2. Type the following in the command line, replacing `<portNumber>` with the value that you want, and press Enter.
  
    ```
    edgecmd Configuration System Port port=<portNumber>
    ```
  
    **Example:** Set port number to 5595
  
    ```
    edgecmd Configuration System Port port=5595
    ```
    
 To verify that the port number has been changed, see [Retrieve existing configuration](xref:RetrieveExistingConfiguration#view-a-specific-facet-configuration).
