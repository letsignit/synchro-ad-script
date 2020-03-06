# PowerShell Script for Synchronizing Active Directory

[Sync-Ad.ps1](https://github.com/letsignit/synchro-ad-script/releases/latest/download/sync-ad.ps1) is a PowerShell script for Synchronizing your active directory with Letsignit.

You have to install a least version 4 of Powershell.
See [here](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-windows-powershell?view=powershell-6)

## Getting Started

Before using the script, you must identify yourself, you can do this by getting your AppId and generating at least one Secret on the Letsignit webapp. Then, add both to the Configuration file, just like shown below: 

```
{
    "appId": "c9b2691877ac4a3ba5997111b0e3248d",
    "appSecret": "&*#7G]SekXoqX427UQ7}X[#7Bz13Kv<5"
}
```

### Configuration File

You can customize your script using a configuration file. The file is in JSON. You have to save the file in the same place that you save the script.

You can download a template of configuration file [here](https://github.com/letsignit/synchro-ad-script/releases/latest/download/config.json)

#### appId & appSecret
For Authentication with Letsignit API we are using an appId and an appSecret.

#### ActiveDirectory

The active directory configuration is used to filter users and groups from your active directory.

If you want to use this part on a Windows 10, RSAT is required. For more information see [here](https://docs.microsoft.com/en-us/windows-server/remote/remote-server-administration-tools)

```
"ActiveDirectory": {
    "Users":{
        "Filter":"mail -like '*@letsignit.com'",
        "SearchBase":"",
        "PropertiesOverride": [],
        "PropertiesAppend": []
    },
    "Groups":{
        "Filter":"mail -like '*letsignit*'",
        "SearchBase":"",
        "PropertiesOverride": [],
        "PropertiesAppend": []
    }
}
```

#### Filter
The filter is the [Get-ADUSer](https://docs.microsoft.com/en-us/powershell/module/addsadministration/get-aduser) or [Get-ADGroup](https://docs.microsoft.com/en-us/powershell/module/addsadministration/get-adgroup) Filter parameter. Here, you can specify the users you want to get with the script.
If you want to select all users, you can set * as the value.
If you want to create a filter you have to make a filter on ADUser properties using [Comparison Operators](https://docs.microsoft.com/fr-FR/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-4.0)

```
"Filter":"*"
```

#### SearchBase
The SearchBase is the [Get-ADUSer](https://docs.microsoft.com/en-us/powershell/module/addsadministration/get-aduser) or [Get-ADGroup](https://docs.microsoft.com/en-us/powershell/module/addsadministration/get-adgroup) SearchBase parameter. Here, you specify an Active Directory 'Distinguished Name' to search under. If you don't specify a SearchBase, the script will get the current Domain DN.

```
"SearchBase":"CN=Users,DC=virtualdevlsi,DC=devlsi"
```

#### PropertiesOverride
By default, the script will select a list of properties. You can override these and put only the properties you want to synchronize.
```
"PropertiesOverride": ["DisplayName", "thumnailPhoto"],
```

#### PropertiesAppend
In addition to overriding properties you can append some properties to the default properties. For example, you can use this to synchronize extension attributes.
```
"PropertiesAppend": ["extensionAttribute1", "extensionAttribute15"],
```

**Note:** You have to know that even if you override or append the properties, Letsignit has to synchronize 3 mandatory properties : **DistinguishedName, ObjectGUID, mail** used to identify the user and  **DistinguishedName, ObjectGUID, Members** to identify the group and his members.


#### TimeOut
You can specify a timeout for POST requests. The default value, 0, specifies an indefinite time-out.

```
"TimeOut":120
```



At this moment you can deploy the script and run it to publish users and groups on  Letsignit.

## Deployment
Download the script ([link](https://github.com/letsignit/synchro-ad-script/releases/latest/download/sync-ad.ps1)) and put it on a Server that can access to your Active Directory Server or it can be the Active Directory itself. 
Then, fill out the config file ([link](https://github.com/letsignit/synchro-ad-script/releases/latest/download/config.json)) with your authentication parameters and specify the filters you want to use.
You can run the script each time you want to update your users and groups on Letsignit, you can also create a scheduled task.

If you want to know more about running a Powershell script from the task scheduler see [here](https://community.spiceworks.com/how_to/17736-run-powershell-scripts-from-task-scheduler)
