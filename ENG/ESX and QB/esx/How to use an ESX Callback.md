#ESX #Callback  #en
# Example:

Suppose you want to create a command for team chat on the client-side that can only be executed by the "Admin" group. First, we create the command with the name "teamchat," which outputs the message "I can read team chat":

```lua
RegisterCommand("teamchat", function(source, args, rawCommand)
    -- Your code goes here
    print("I can read team chat")
end)
```

Now, if we enter /teamchat in the game, "I can read team chat" will be displayed in our F8 console, regardless of whether we are an admin or not.

To check group membership (group membership can only be checked on the server-side), we need to create a callback on the server-side and return the information to the client using a callback.

Here's how you create the callback on the server-side (our callback is named "teamchat:getGroup"):

```lua
ESX.RegisterServerCallback('teamchat:getGroup', function() -- You can add something inside these parentheses if you're sending something from the client to the server. For this example, we don't need that.
    local _source = source -- "source" is always passed and represents the player's ID who is executing the callback. I use "_source" here to avoid possible conflicts.

    local xPlayer = ESX.GetPlayerFromId(_source) -- Here, we fetch player data from ESX.

    local servergroup = xPlayer.getGroup() -- Here, we define "servergroup" as the player's group.

    local servername = xPlayer.getName() -- Here, we define "servername" as the player's name, which we can use later.

    cb(servergroup, servername) -- Here, we trigger the callback and send the values "servergroup" and "servername" back to the client.
end)
```

Now, let's revisit our command and integrate the callback on the client-side:

```lua
RegisterCommand("teamchat", function(source, args, rawCommand)
    -- Your code goes here
    ESX.TriggerServerCallback('teamchat:getGroup', function(clientgroup, clientname) -- Here, we specify two variables. Their names don't matter, but the order is important as it matches what the server provides.
        if clientgroup == "admin" then -- We check if the group is "admin."
            -- If yes
            print("Hooray! " .. clientname .. ", you are now allowed to read team chat!")
        else -- Otherwise (if it's not the "admin" group)
            print("Unfortunately, you do not have permission to read team chat. Your group: " .. clientgroup)
        end
    end)
end)
```

Now, only people in the "admin" group are allowed to use our team chat!

To learn more about ESX callbacks, please read the [ESX Wiki](https://documentation.esx-framework.org/legacy/installation/).