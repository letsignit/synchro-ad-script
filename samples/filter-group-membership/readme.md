# Filter Group

This sample show you how to make a filter on a group membership.

```
"ActiveDirectory": {
    "Users":{
        "Filter":"memberOf -like 'CN=Groupe de test,OU=Groupes de distribution,OU=Utilisateurs,DC=lsidev,DC=local'",
        "SearchBase":"DC=lsidev,DC=local"
    }
}
```
If you want to make a filter on a group membership you have to filter on the **memberOf** property.

In this example below the filter is on the group named "Groupe de test".

You can also add a base filter, here the domain. Can be a specific OU.