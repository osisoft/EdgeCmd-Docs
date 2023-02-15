---
uid : SecretsManagement
---

# Configure secrets

Use EdgeCmd utilty to manage secrets.

**Note:** The examples in this topic are using the default port number `5590`. If you specified a different port number for your adapter or EDS, you need to add it in the command. For example:
```cmd
edgecmd -port 5591 <RestOfTheCommand>
```

## Updating secrets configuration

Complete the following steps to create or update the entire secret configuration.

1. Access EdgeCmd utility through the command line.
2. Type the `set` keyword.
3. Add the `Secrets` facet.
4. Add the key-value pairs if needed. Then, press Enter.

**Example 1:** Update using a file. 

**Note:** If the secret configuration already exists, using this command will replace the entire old secret configuration.
```cmd
edgecmd set Secrets -file <filePath>
```

**Example 2:** Update using key-value pairs. 

**Note:** If the secret configuration already exists, this command will append the secret to the current secret configuration. If the secret configuration does not exist, it will create the configuration with this single secret. If a secret with this secretId already exists, it will update the values.
```cmd
edgecmd set Secrets -id <secretId> -value <secretValue> -description <description> -expirationDate <expirationDate>
```

## Deleting secrets

Complete the following steps to permanently delete secrets.

1. Access EdgeCmd utility through the command line.
2. Type the `remove` keyword.
3. Add the `Secrets` facet.
4. Add the key-value pairs if needed. Then, press enter.

**Example 1:** Deleting a single secret.
```cmd
edgecmd remove Secrets -id <secretId>
```

**Example 2:** Deleting the entire set of secrets in the secret configuration.
```cmd
edgecmd remove Secrets
```
**Note:** You can specify `-y` parameter to skip the confirmation prompt.

## Other Secret Commands

1. Returning a single secret.
```cmd
edgecmd get Secrets -id <secretId>
```

2. Returning the entire secrets configuration.
```cmd
edgecmd get Secrets
```

3. Returning secrets help information.
```cmd
edgecmd help Secrets
```