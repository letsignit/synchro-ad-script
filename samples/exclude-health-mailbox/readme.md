# Exclude health mailbox

This sample show you how to exclude health mailbox from users.

```
"ActiveDirectory": {
    "Users":{
        "Filter":"mail -notlike 'HealthMailbox*'",
        "SearchBase":"DC=lsidev,DC=local"
    }
}
```

You can also add a base filter, here the domain. Can be a specific OU.