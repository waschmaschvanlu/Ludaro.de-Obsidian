>[!info] this is filled with my notes not rdy yet


This error comes when a script is old and uses the old event to remove an item,

to fix it you have to go into the corresponding server lua file of your script and replace 
> [!warning] ( 1 and 2 are variable names, remember these they are important later on!)
```lua
TriggerServerEvent("QBCore:Server:AddItem", 1, 2)
```
delete it, and try to remove the Item from the Serverside.