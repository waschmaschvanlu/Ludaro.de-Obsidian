#ESX #getsharedobject  #en
To use ESX and its functions, you need to "load" them via an export (or in earlier versions, via an event). This is achieved with the following code snippet:

```lua
if (GetResourceState("es_extended") == "started") then
    if (exports["es_extended"] and exports["es_extended"].getSharedObject) then
        ESX = exports["es_extended"]:getSharedObject()
    else
        TriggerEvent("esx:getSharedObject", function(obj) ESX = obj end)
    end
end
```

This code checks whether an older version is being used (by checking if the export exists) and uses the appropriate version.

To successfully utilize ESX, please refer to the [ESX Wiki](https://documentation.esx-framework.org/legacy/installation/) to learn what you can do, :) 

To find out more, please read the [ESX Wiki](https://documentation.esx-framework.org/legacy/installation/).