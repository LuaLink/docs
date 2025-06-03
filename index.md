---
label: Home
icon: home
order: 100
---
# LuaLink v2
**LuaLink** is an experimental plugin that provides a basic Lua scripting runtime for **Paper-based** Minecraft servers. It is designed for small and simple tasks and serves as a much more powerful alternative to **Skript** and other scripting plugins. 

Scripting runtime is based on **[LuaJava](https://github.com/gudzpoz/luajava)** with **[LuaJIT](https://github.com/LuaJIT/LuaJIT)**. For more details on implementation specifics or differences, please refer to their respective documentation.  

<br />

<style>
    .features {
        .table-wrapper, td, th {
            border-color: transparent !important;
        }
        .docs-icon {
            font-size: 1.25em;
        }
    }
</style>
:::features
{.compact}
|                             |     |
| --------------------------: | --- |
| :icon-rocket:               | <u>**High Performance**</u><br>LuaLink leverages LuaJava and LuaJIT, which are implemented primarily in C, ensuring fast and efficient execution. |
| :icon-thumbsup:             | <u>**User-Friendly API**</u><br>Simplifies scripting with an intuitive and easy-to-use API. |
| :icon-terminal:             | <u>**Simple Command Registration**</u><br>Register commands effortlessly with a single function. |
| :icon-zap:                  | <u>**Event Listening**</u><br>Listen to Bukkit, Spigot, Paper, or even custom plugin events. |
| :icon-file:                 | <u>**Script Organization**</u><br>Split scripts into multiple files. Each script requires a `main.lua` entry point but can load additional files using Lua’s `require` function. |
| :icon-package-dependencies: | <u>**Java Library Integration**</u><br>Extend LuaLink’s capabilities by using any Java library. Whether it’s for a Discord bot, HTTP server, or anything else you can imagine. |
| :icon-globe:                | <u>**Access Everything**</u><br>Full access to Bukkit API, built-in libraries and loaded plugins. |
:::

<br />

## Installation
Before you begin, make sure you have met the following requirements:
- **[Paper](https://papermc.io/)** based server running **1.20** or higher, and **Java 21**.  
- Basic understanding of **Lua** scripting and general programming concepts is beneficial.

Plugin can be downloaded from following sources:

{.list-icon}
- [**:icon-download: Modrinth** (modrinth.com)](https://modrinth.com/plugin/lualink)
- [**:icon-download: Hangar** (hangar.papermc.io)](https://hangar.papermc.io/Saturn/LuaLink)

<br />

## Quick Start
After you have installed the plugin, you can start writing your first script.

- Script life-cycle can be managed using `/lualink load`, `/lualink unload` and `/lualink reload` commands.
- Each script is stored in a separate folder inside the `plugins/LuaLink/scripts` directory.
- Entry point of the script is a file named `main.lua`.

```lua plugins/LuaLink/scripts/my_script/main.lua
-- Called after the script has been successfully loaded.
script:onLoad(function()
    -- Logging message to the console.
    print("Hello, World!")
end)

```
It's quite simple, isn't it? For this particular case, we can simplify it even further by extracting the logic away from the `onLoad` block.

```lua plugins/LuaLink/scripts/my_script/main.lua
-- Logging message to the console.
print("Hello, World!")
```
Want to do something more complex? More information on how to write scripts can be found on the **[Getting Started](getting-started.md)** page.
