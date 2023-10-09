#ESX #getsharedobject  #ger
Um ESX und deren Funktionen verwenden zu Können muss man diese über einen Export (oder in früheren Versionen über ein Event) sozusagen „laden“ dies wird mit diesem Code-Snippet erreicht:
```lua
if (GetResourceState("es_extended") == "started") then
    if (exports["es_extended"] and exports["es_extended"].getSharedObject) then
        ESX = exports["es_extended"]:getSharedObject()
    else
        TriggerEvent("esx:getSharedObject", function(obj) ESX = obj end)
    end
end
```

Dieses checkt, ob eine alte Version benutzt wird (indem es checkt, ob der Export existiert) und benutzt die richtige Variante.

Um ESX erfolgreich zu verwenden, schau in der [esx wiki](https://documentation.esx-framework.org/legacy/installation/) nach was du machen kannst, :) 

um mehr darüber raus zu finden lese bitte die [ESX-Wiki](https://documentation.esx-framework.org/legacy/installation/)