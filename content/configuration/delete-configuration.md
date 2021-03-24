---
uid: DeleteConfiguration
---

# Delete configuration
Use the EdgeCMD utility to delete configuration entries for Edge Data Store.

## Delete configuration entry

Complete the following to delete a configuration entry from a collection configuration in Edge Data Store. For example, you can delete a single health endpoint of the 'HealthEndpoints' facet within the 'System' component.

1. Access the EdgeCmd utility through a command line tool.
2. Type the following command, replacing the `componentId` and `facetName` followed by the ID of the entry to be removed, and press Enter.

   ```bash
   edgecmd Configuration <componentId> <facetName> delete
   ```

   **Example:** Delete endpoint_1 of the HealthEndpoints facet from the System:

   ```bash
   edgecmd Configuration System HealthEndpoints Id=endpoint_1 delete
   ```

## Delete configuration file

Complete the following to delete a configuration file from Edge Data Store. For example, you can delete the configuration file of the 'HealthEndpoints' facet within the 'System' component.

1. Access the EdgeCmd utility through a command line tool. 
2. Type the following command, replacing the `componentId` and `facetName` to delete, and press Enter.

   ```bash
   edgecmd Configuration <componentId> <facetName> delete
   ```
   
   **Example:** Delete the HealthEndpoints facet configuration file:

   ```bash
   edgecmd Configuration System HealthEndpoints delete
   ```

