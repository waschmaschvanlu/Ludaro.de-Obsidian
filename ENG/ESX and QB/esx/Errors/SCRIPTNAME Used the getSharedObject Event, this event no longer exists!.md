#sharedobject #getsharedobject #oldesx #help #error #Scripting #en

# What Does This Error Mean?

The error message mentioned above states:

**SCRIPTNAME** is using the event **getSharedObject**, but this event no longer exists!

This error occurs because in newer versions of ESX (from version 1.9 onwards), an event called **getSharedObject** is no longer used. Instead, it has been replaced by an export.

# Why Does This Error Occur?

This error occurs because **events** in FiveM are considered **inefficient**, meaning they can impact performance. For this reason, the event that was previously used was replaced with an export. However, it was later discovered that this was a mistake, as the export essentially does the same as the event.

## In scripts, it looks like this:

> [!warning] The event shown here may be implemented differently in various scripts and may deviate from what is shown here.

> [!warning] The event shown here may vary in different scripts, as many scripts implement it differently. Some even write ESX = nil before it, which is not necessary and should be avoided!

### Old Event:
```lua
TriggerEvent("esx:getSharedObject", function(obj) ESX = obj end)
```

### New Export:
```lua
ESX = exports["es_extended"]:getSharedObject()
```

# How Can I Fix This Error?

There are two methods to fix this error:

1. Replace the event in each script with the export.
> [!info] This method is supported and recommended by ESX. It is somewhat more challenging to implement but saves on performance!

2. Rewrite ESX to use the event again.
> [!warning] This method is NOT recommended by ESX, as it can impact performance.

Both methods are explained in detail below:

## 1. Replacing the Event in Each Script with the Export

To achieve this, you need to search for the old event in each script (client and server Lua files):

```lua
TriggerEvent("esx:getSharedObject", function(obj) ESX = obj end)
```

Find this line and replace it with the new export:

```lua
ESX = exports["es_extended"]:getSharedObject()
```

This can sometimes be challenging because this line may be in an encrypted file that you don't have access to. In this case, consider Method 2.

## 2. Rewriting ESX to Use the Event Again
> [!warning] This method should only be considered if Method 1 doesn't work or if you are willing to sacrifice performance!

To achieve this, open your ESX folder (es_extended) and first, look in the file `client/common.lua` for the following code:

> [!info] For clarification, this is the old event that we are rewriting to make it work like it used to!

```lua
AddEventHandler("esx:getSharedObject", function()
	local Invoke = GetInvokingResource()
	print(("[^1ERROR^7] Resource ^5%s^7 Used the ^5getSharedObject^7 Event, this event ^1no longer exists!^7 Visit https://documentation.esx-framework.org/tutorials/tutorials-esx/sharedevent for how to fix!"):format(Invoke))
end)
```

Replace this code section with:

```lua
AddEventHandler("esx:getSharedObject", function(cb)
	cb(ESX)
end)
```

Perform the same step in the file `es_extended/server/common.lua` as well.