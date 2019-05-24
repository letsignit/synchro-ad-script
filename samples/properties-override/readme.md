# Override user properties

This sample show you how to overrides user properties.

```
"ActiveDirectory": {
    "Users":{
        "Filter":"*",
        "SearchBase":"DC=lsidev,DC=local",
        "PropertiesOverride": ["Name", "DisplayName", "thumbnailPhoto"],
        "PropertiesAppend": []
    }
```

In this example below the script will override the default properties and retrieve **Name**, **DisplayName** and **thumbnailPhoto**.

**Note:** You have to know that even if you override the properties, Letsignit has to synchronize 3 mandatory properties : **DistinguishedName, ObjectGUID, mail** used to identify the user and  **DistinguishedName, ObjectGUID, Members** to identify the group and his members.