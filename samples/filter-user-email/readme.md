# Filter user Email

This sample show you how to make a filter on user email.

```
"ActiveDirectory": {
    "Users":{
        "Filter":"mail -like '*@domain.com'",
        "SearchBase":"DC=lsidev,DC=local"
    }
}
```
In this example below you get all users that have their email containing '@domain.com'

You can also add a base filter, here the domain. Can be a specific OU.