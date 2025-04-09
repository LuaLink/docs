---
label: Home
icon: home
order: 100
---
!!!danger Important
This documentation page is still a work in progress and may contain outdated information.
!!!

# LuaLink v2
LuaLink is an experimental plugin that provides a basic Lua scripting runtime for Paper-based Minecraft servers. It is designed for small and simple tasks and serves as an alternative to Skript and other scripting plugins. 

Scripting runtime is based on [LuaJava](https://github.com/gudzpoz/luajava) with [LuaJIT](https://github.com/LuaJIT/LuaJIT). For more details on implementation specifics or differences, please refer to their respective documentation.  

<br />

## Features
{.list-icon}
- :icon-code-square: Quick and easy scripting with Lua syntax. 
- :icon-package: Full access to Bukkit API, built-in libraries and ~~loaded plugins~~. (work in progress)
- :icon-package-dependents: Create your own or load external Java and Lua libraries.
- :icon-sync: Loading and unloading of Lua scripts at runtime.
- :icon-gear: Built-in utilities to simplify common tasks.

<br />

## Installation
Before you begin, make sure you have met the following requirements:
- **[Paper](https://papermc.io/)** based server running **1.20** or higher, and **Java 21**.  
- Basic understanding of **Lua** scripting and general programming concepts is beneficial.

Plugin can be downloaded from following sources:

{.list-icon}
- [**:icon-download: Modrinth** (modrinth.com)](https://modrinth.com/plugin/lualink)
- [**:icon-download: Hangar** (hangar.papermc.io)](https://hangar.papermc.io/Saturn/LuaLink)
- [**:icon-download: GitHub Releases** (github.com)](https://github.com/LuaLink/LuaLinkV2/releases)

<br />

## Quick Start
After you have installed the plugin, you can start writing your first script.

- Each script is stored in a separate folder inside the `plugins/LuaLink/scripts` directory. 
- Entry point of the script is a file named `main.lua` or `init.lua`.
- Script life-cycle can be managed using `/lualink load`, `/lualink unload` and `/lualink reload` commands.

```lua plugins/LuaLink/scripts/my_script/init.lua
local Bukkit = import "org.bukkit.Bukkit"

-- Called after the script has been successfully loaded.
script:onLoad(function()
    -- Logging message to the console.
    script:logger:info("Hello, World!")
end)

```
It's quite simple, isn't it? For this particular case, we can simplify it even further by extracting the logic away from the `onLoad` block.

```lua plugins/LuaLink/scripts/my_script/init.lua
local Bukkit = import "org.bukkit.Bukkit"

-- Logging message to the console.
script:logger:info("Hello, World!")
```
Want to do something more complex? More information on how to write scripts can be found on the **[Getting Started](getting-started.md)** page.
