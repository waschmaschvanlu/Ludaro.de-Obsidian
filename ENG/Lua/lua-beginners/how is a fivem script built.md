#WhatIs #Scripting #LearnScripting #en

FiveM scripts are built on two frames: a server and a client. Both communicate with each other. The server handles tasks like player synchronization and database management, while the client handles in-game actions such as spawning cars (after checking with the server if it's allowed) or changing weather.

Shared scripts serve as a bridge between both, mainly used for configurations. They ensure that you don't have separate configurations on the client and server sides, which would be impractical.

Things on the server-side cannot be directly accessed on the client-side for security reasons unless an event passes the information.

In the `fxmanifest.lua` file, you specify the script's version, name, and dependencies. The server first reads the `fxmanifest` to determine if the script is usable.

To determine whether a part of the script is server or client-side, you specify it in the `fxmanifest.lua` file, like in this example from your Trucker Job script on GitHub:

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

-- This is NativeUI'@NativeUILua_Reloaded/src/NativeUIReloaded.lua',

-- This is NativeUIReloaded '@NativeUI/NativeUI.lua',

'client.lua'

}

server_scripts {

'server.lua',

-- This is used for mysql'@mysql-async/lib/MySQL.lua'

}
```

You're welcome to check my [GitHub](https://github.com/waschmaschvanlu) to see how scripts are structured in more detail.