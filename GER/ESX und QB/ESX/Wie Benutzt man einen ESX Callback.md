#ESX #Callback  #ger
# Beispiel:

Angenommen, du möchtest einen Befehl für den Team-Chat auf der Client-Seite erstellen, der nur von der Gruppe "Admin" ausgeführt werden kann. Zuerst erstellen wir den Befehl mit dem Namen "teamchat", der eine Nachricht "Ich kann im Teamchat lesen" ausgibt:

```lua
RegisterCommand("teamchat", function(source, args, rawCommand)
    -- Hier kommt unser Code rein
    print("Ich kann im Teamchat lesen")
end)
```

Wenn wir nun ins Spiel gehen und /teamchat eingeben, wird in unserer F8-Konsole "Ich kann im Teamchat lesen" angezeigt, unabhängig davon, ob wir Admin sind oder nicht.

Um die Gruppenzugehörigkeit abzufragen (Gruppenzugehörigkeit kann nur auf der Server-Seite überprüft werden), müssen wir einen Callback auf der Server-Seite erstellen und die Informationen mit einem Callback an den Client zurückgeben.

Hier ist, wie man den Callback auf der Server-Seite erstellt (unser Callback heißt "teamchat:getGroup"):

```lua
ESX.RegisterServerCallback('teamchat:getGroup', function() -- In diese Klammern kannst du etwas einfügen, wenn du vom Client etwas zum Server sendest. Für dieses Beispiel benötigen wir das nicht.
    local _source = source -- "source" wird immer mitgegeben und ist die Spieler-ID des Spielers, der den Callback ausführt. Ich benutze hier "_source", um mögliche Konflikte zu vermeiden.

    local xPlayer = ESX.GetPlayerFromId(_source) -- Hier fragen wir die Spielerdaten von ESX ab.

    local servergroup = xPlayer.getGroup() -- Hier definieren wir "servergroup" als die Gruppe des Spielers.

    local servername = xPlayer.getName() -- Hier definieren wir "servername" als den Namen des Spielers, den wir später verwenden können.

    cb(servergroup, servername) -- Hier rufen wir den Callback auf und senden die Werte "servergroup" und "servername" an den Client zurück.
end)
```

Nun schauen wir uns erneut unseren Befehl an und integrieren den Callback auf der Client-Seite:

```lua
RegisterCommand("teamchat", function(source, args, rawCommand)
    -- Hier kommt unser Code rein
    ESX.TriggerServerCallback('teamchat:getGroup', function(clientgroup, clientname) -- Hier tragen wir zwei Variablen ein. Wie sie heißen, ist egal, aber die Reihenfolge ist wichtig, da sie vom Server übernommen wird.
        if clientgroup == "admin" then -- Wir überprüfen, ob die Gruppe "admin" ist.
            -- Wenn ja
            print("Hurra! " .. clientname .. ", du darfst jetzt den Teamchat lesen!")
        else -- Andernfalls (falls es keine "admin"-Gruppe ist)
            print("Du hast leider keine Berechtigung, den Teamchat zu lesen. Deine Gruppe: " .. clientgroup)
        end
    end)
end)
```

Jetzt dürfen nur Personen mit der Gruppe "admin" unseren Teamchat benutzen!

Um mehr über ESX-Callbacks zu erfahren, lies bitte die [ESX-Wiki](https://documentation.esx-framework.org/legacy/installation/).