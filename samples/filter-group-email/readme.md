# Filter group Email

This sample show you how to make a filter on group email.

```
"ActiveDirectory": {
    "Groups":{
        "Filter":"mail -like '*@domain.com'",
        "SearchBase":"DC=lsidev,DC=local"
    }
}
```
In this example below you get all groups that have their email containing '@domain.com'

You can also add a base filter, here the domain. Can be a specific OU.