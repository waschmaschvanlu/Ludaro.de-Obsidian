#wasist #Scripting  #scriptenlernen  #ger
Fivem-Skripte sind auf 2 Frames aufgebaut, einem Server und einem Client

beide kommunizieren miteinander, der Server kümmert sich z. B. darum, dass alle Spieler synchronisiert werden, und dass die SQL-Datenbank funktioniert,

der Client macht alles, was mit dem Spiel zu tun hat, wie z. B. das Spawnen von Autos (wobei er den Server vorher fragt, ob das in Ordnung ist) oder das Ändern des Wetters und solche Sachen

shared_scripts sind eigentlich beides gleichzeitig, es wird nur für Configs verwendet. Weil man nicht eine Config auf der Client- und Serverseite haben will, ist das dumm.

Dinge auf der Serverseite können NICHT auf der Clientseite verwendet werden (aus Sicherheitsgründen), es sei denn, ein Event gibt sie weiter

in der fxmanifest.lua steht auch, welche Version des Skripts du gerade benutzt, wie es heißt und was es braucht (dependencies)

Wenn ein Skript überhaupt nicht startet, dann schau in das fxmanifest, weil der Server die fxmanifest zuerst liest und dann entscheidet, ob es brauchbar ist oder nicht.

Welcher Teil des Skripts server- oder clientseitig ist, wird in der fxmanifest.lua wie folgt angezeigt: (Beispiel aus meinem Truckerjob auf github)

```lua
fx_version 'cerulean'

game 'gta5'

name "Trucker job"

author 'Sukra, Ludaro'

description 'Trucker Job for esx'

version '3.0'

shared_scripts {

'config.lua'

}

client_scripts {

-- Dies ist NativeUI'@NativeUILua_Reloaded/src/NativeUIReloaded.lua',

-- Dies ist NativeUIReloaded '@NativeUI/NativeUI.lua',

'client.lua'

}

server_scripts {

'server.lua',

-- dies wird für mysql benutzt'@mysql-async/lib/MySQL.lua'

}
```

Du kannst immer gern auf mein [github](https://github.com/waschmaschvanlu) schauen und sehen wie es genau aufgebaut ist,