---
uid: DeleteConfiguration1-1
---

# Delete configuration

Use the EdgeCmd utility to delete adapter or EDS configurations or configuration entries that you no longer need.

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter or EDS, you need to add it in the command. For example:

```cmd
edgecmd -port 5591 <RestOfTheCommand>
```

## Delete configuration entry

Complete the following steps to delete a configuration entry from a collection configuration. For example, you can delete a single health endpoint of the 'HealthEndpoints' facet within the 'System' component.

1. Access EdgeCmd utility through the command line.
2. Type the `remove` keyword.
3. Add the `<facetName>` and `<componentId>`, replacing both with their respective values.
4. Add the ID of the entry to be removed. Then press Enter.

   ```cmd
   edgecmd remove <facetName> -cid <componentId> -id <entry>
   ```

   **Example:** Delete 'endpoint_1' of the 'HealthEndpoints' facet in the 'System' component:

   ```cmd
   edgecmd remove HealthEndpoints -cid System -id endpoint_1
   ```

   **Note:** If the facet is part of the System component, the command does not require `<componentId>`, for example:

   ```cmd
   edgecmd remove HealthEndpoints -id OcsEndpoint
   ```

## Delete entire configuration

Complete the following steps to delete the entire configuration of a system facet. For example, you can delete the configuration of the 'HealthEndpoints' facet within the 'System' component.

1. Access EdgeCmd utility through the command line.
2. Type the `remove` keyword.
3. Add the `<facetName>` and `<componentId>`, replacing both with their respective values. Then press Enter.

   ```cmd
   edgecmd remove <facetName> -cid <componentId>
   ```

   **Example:** Delete the 'HealthEndpoints' facet configuration file from the 'System' component:

   ```cmd
   edgecmd remove HealthEndpoints -cid System
   ```

   **Note:** To skip the confirmation prompt, specify the `-y` parameter in the command.
