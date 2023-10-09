# Scripting #LearnScripting #Tutorial

# What is Needed to Create Your First FiveM Script?

- [ ] A test server, either on your own PC (see "Hosting a FiveM Server on Your Own PC") or on a dedicated server.
- [ ] A good text editor (Visual Studio Code is recommended, but you can use any you prefer).
- [ ] A program or website to access your database (e.g., phpMyAdmin or HeidiSQL).

# Beginner's Guide: Creating Your First FiveM Script

> [info] Important prerequisites:
> You should have already read [[What Is...]].

If you want to create your first FiveM script, you should start by thinking about the project you want to implement. In the "Beginner Projects to Follow" category, you'll find ideas and tutorials that can help you with your project. It's advisable not to choose overly complex projects since making mistakes is allowed and can be a valuable learning experience. You can do this on a test server on your own PC (see "Hosting a FiveM Server on Your Own PC") or on another server.

## Documentation

Before you begin creating your script, it's helpful to clearly define your idea, either in your mind or with notes. Consider:

- What should my script do?
- What code resources do I need for it?

Let's explain this using an example of a team chat script.

#### A team chat script requires:

- An existing chat system.
- A group system (e.g., ESX or QB).

#### What should my script do?

When I type "/teamchat MESSAGE," this message should be forwarded to all admins. To do this, I need to check if the person belongs to the admin group and then send the message to all admins.

It's not necessary to document everything in detail, but having a rough idea will help you maintain the script's structure and know where to start.

## Script Creation

To create the script, navigate to the "resources" folder of your FiveM server and create a folder. The name should not contain spaces or special characters and should be easy to remember.

Inside this folder, create a file named "fxmanifest.lua."

> [!info] Visual Studio Code allows you to open entire folders for better organization. I recommend doing this (click on "File" -> "Open Folder" in the top left and select your resources folder).

This file specifies what your script consists of:

```lua
fx_version 'cerulean'

game 'gta5'

name "Teamchat" -- The name of our script

author 'Ludaro' -- Our name

description 'A team chat for cool people!' -- A brief description
```

Now, we need to consider:

- What Lua files do we need? (Client, Server, Shared).

For our team chat script, we need a server Lua file to retrieve the group and a client Lua file to create the command. Additionally, we need a configuration file that must be "shared" so it can be read by both the client and server.

Configure this in our "fxmanifest.lua" document, below what we've already written:

```lua
client_scripts {
    'client.lua'
}

server_scripts {
    'server.lua'
}

shared_scripts {
    'config.lua'
}
```

Now our structure is complete, and we can start with the "client.lua" file!

But before we do that, let's take a closer look at the difference between server and client scripts.

# Difference Between Server and Client Scripts

## Why Does This Difference Exist?

The difference between server and client files is that everything executed on the client side (in the game) can potentially be read, stolen, or even manipulated by others. This poses security concerns. Therefore, there is a clear separation between the code that runs on the server and

 the code that runs on the client. However, there are interfaces to overcome this separation, known as "events." Here's a brief overview of the task distribution between client and server:

## Client

- Everything related directly to gameplay (e.g., automatically creating objects, playing animations, etc.).
- Anything related to the appearance and behavior of the player's own character.

## Server

- Anything related to player data (e.g., group membership, profession, name).
- Anything related to the database.
- Everything related to synchronizing and coordinating all players.

I hope this clarifies the difference between server and client for you! If you have further questions, I'm here to help.

> [!info] This wiki is not yet complete and is still being developed. Check back later!

But how does it actually work? Confusing, isn't it? Don't worry; we'll take a closer look in the following steps.