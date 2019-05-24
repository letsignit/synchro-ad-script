# Append user properties

This sample show you how to append new properties to default user properties.

```
"ActiveDirectory": {
    "Users":{
        "Filter":"*",
        "SearchBase":"DC=lsidev,DC=local",
        "PropertiesOverride": [],
        "PropertiesAppend": ["extensionAttribute1"]
    }
```

In this example below the script will retrieve the **extensionAttribute1** in addition to the default properties.