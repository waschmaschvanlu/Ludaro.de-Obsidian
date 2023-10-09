#ESX #Update #en
> [!info] This website is still 0% complete and contains only my notes.

# Migrating from EssentialMode (1.1) to Legacy

Unfortunately, it is not possible to update from ESX 1.1 to newer versions. It is recommended to set up the entire server anew and transfer all necessary resources individually because the structure has completely changed from 1.1 to ESX Legacy.

One way to do this in txAdmin is to use the "Master Actions" and reconfigure the server. Note that this DOES NOT delete the server folder but only creates a new one. There, you can select ESX Legacy and start fresh with the latest version of ESX.

# Migrating from ESX 1.2 to ESX Legacy

To migrate from ESX 1.2 to ESX Legacy, go to the [esx_core](https://github.com/esx-framework/esx_core) GitHub and download the entire repository. Then, import the [SQL](https://github.com/esx-framework/esx_core/blob/main/database.sql) into your database and download [oxmysql](https://github.com/overextended/oxmysql/releases/tag/v2.7.5). Start oxmysql BEFORE es_extended and remove the es_extended folder. Instead, upload the [core](https://github.com/esx-framework/esx_core/tree/main/core) folder to your server and start that instead of es_extended.

Check if there are already scripts in the core folder. If so, either delete them in the core folder or in your resource folder.

To learn more, please read the [ESX Wiki](https://documentation.esx-framework.org/legacy/installation/).