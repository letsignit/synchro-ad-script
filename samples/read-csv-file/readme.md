# Read a csv file

This sample show you how to configure the script to read a csv file.

```
 "Csv" : {
    "Delimiter" : ";"
}
```

By addin this to your configuration file, the script will read a file **users.csv** to get users.

**Delimiter**  : The demiliter used to generate the **users.csv** file.
If no provided **','** value will be used.

**Note:** You can't have both Csv and AzureDirectory configurated in configuration file.
