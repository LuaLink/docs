---
icon: gear
order: 99
---
# Getting Started
This page contains a basic introduction to writing **Lua** scripts with **LuaLink**.

It is important to know the basics of **Java** programming and **Bukkit API** because this is how you will interact with the Minecraft server.

Basic **Lua** knowledge is an obvious prerequisite, but it should be relatively easy to pick up assuming you have some experience with programming.

{.list-icon}
- [**:icon-paperclip: Lua** (devdocs.io)](https://devdocs.io/lua/)
- [**:icon-paperclip: Java 21** (devdocs.io)](https://devdocs.io/openjdk~21/)
- [**:icon-paperclip: Paper Docs** (docs.papermc.io)](https://docs.papermc.io/paper/dev/api)
- [**:icon-paperclip: Paper Javadocs** (jd.papermc.io)](https://jd.papermc.io/paper/1.21.5/)

<br />

| Navigation {.compact}                                        | 
| ------------------------------------------------------------ |
| [1. Creating Scripts](#creating-scripts)                     |
| [2. Script Life-cycle](#script-life-cycle)                   |
| [3. Importing and Requiring](#importing-and-requiring)       |
| [4. Constructors and Instances](#constructors-and-instances) |
| [5. Commands](#commands)                                     |
| [6. Events](#events)                                         |
| [7. Scheduler](#scheduler)                                   |

<br />

### Creating Scripts
There are a couple of things to keep in mind when using LuaLink.
- Each script is stored in a separate folder inside the `plugins/LuaLink/scripts` directory.  
  <sup>For example `/plugins/LuaLink/scripts/example/main.lua` will be loaded as `example` script.</sup>
- Script life-cycle can be managed using `/lualink` command.  
  <sup>Full command reference is available on the **[Commands](commands.md)** page.</sup>
- Entry point of the script is a file named `main.lua`.  
  <sup>More files can be imported using the `require` keyword.</sup>

<br />

### Script Life-cycle
Scripts are automatically loaded after server has been fully started. They can also be loaded, unloaded or reloaded manually using commands.
```lua
-- Called after the script has been successfully loaded.
script:onLoad(function()
    script.logger:info("Script has been loaded.")
end)

-- Called before the script is attempted to be unloaded.
script:onUnload(function()
    script.logger:info("Script is about to be unloaded.")
end)
```

<br />

### Importing and Requiring
Each referenced **Java** class must be imported using the `import` keyword.
```lua
local Bukkit = import("org.bukkit.Bukkit")
local MiniMessage = import("net.kyori.adventure.text.minimessage.MiniMessage")

script:onLoad(function(event)
    -- Creating Component using MiniMessage serializer. https://docs.advntr.dev/minimessage/index.html
    local component = MiniMessage:miniMessage():deserialize("<rainbow>Did you know you can make rainbow text?!")
    -- Sending component to everyone, including console.
    Bukkit:getServer():sendMessage(component)
end)
```
Each referenced **Lua** class or library, must be required using the `require` keyword.
```lua
local Counter = require("example_library")

script:onLoad(function()
    -- Creating a new instance of the Counter class.
    local counter = Counter.new()
    -- Incrementing the counter three times.
    counter:increment()
    counter:increment()
    counter:increment()
    -- Printing current value of the counter to the console.
    script.logger:info(counter:get() .. " is the current value of the counter.")
end)
```

<br />

### Constructors and Instances
New instances of Java classes can be created as follows.
```lua
local Bukkit = import("org.bukkit.Bukkit")
local Keyed = import("net.kyori.adventure.key.Keyed")
local NamespacedKey = import("org.bukkit.NamespacedKey")

script:onLoad(function()
    -- Creating new instance of NamespacedKey class.
    local key = NamespacedKey("minecraft", "overworld")
    -- Getting instance of the primary world.
    local world = Bukkit:getWorld(key)
    -- Checking if World is instance of Keyed. (SPOILER: IT IS)
    if (Keyed.class:isInstance(world) == true) then 
        -- Sending loaded chunks count to the console.
        script.logger:info("World " .. world:key():asString() .. " has " .. world:getChunkCount() .. " chunks loaded.")
    end
end)
```

<br />

### Commands
Non-complex commands can be created with little effort using built-in API.
```lua
local Bukkit = import("org.bukkit.Bukkit")

-- Function to handle command tab-completion.
function onTabComplete(sender, args)
    -- No suggestions will be shown for this command.
    return {}
end

script:registerCommand(function(sender, args)
    -- Joining arguments to string using space as delimiter.
    -- java.luaify(...) function is responsible for converting Java objects to Lua. In this case, it converts String[] to a Lua table.  
    local message = table.concat(java.luaify(args), " ")
    -- Sending message back to the sender.
    sender:sendRichMessage(message)
end, {
    -- REQUIRED
    name = "echo",
    -- OPTIONAL
    aliases = {"e", "print"},
    permission = "scripts.command.echo",
    description = "Prints specified message to the sender.",
    usage = "/echo [message]",
    tabComplete = onTabComplete
})
```

<br />

### Events 
Bukkit events can be hooked into relatively easily.
```lua
-- Called when player joins the server.
script:registerListener("org.bukkit.event.player.PlayerJoinEvent", function(event)
    -- Getting player associated with the event. 
    local player = event:getPlayer()
    -- Playing firework sound to the player.
    player:playSound(player:getLocation(), "entity.firework_rocket.launch", 1.0, 1.0)
    -- Sending welcome message to the player.
    player:sendRichMessage("<green>Welcome back to the server, " .. player:getName() .. "!")
end)
```

<br />

### Scheduler
Scheduler can be used to register single-use, delayed or repeating tasks.
```lua
-- Schedules a task to be run on the next tick.
scheduler:run(function(runnable)
    -- Whatever belongs to the task goes here.
end)

-- Schedules a task to be run after 20 ticks has passed. 
scheduler:runDelayed(function(runnable)
    -- Whatever belongs to the task goes here.
end, 20)

-- Schedules a task to be run after 20 ticks has passed, and repeated every 160 ticks.
scheduler:runRepeating(function(runnable)
    -- Whatever belongs to the task goes here.
end, 20, 160)
```

Tasks can also be run asynchronously, but please note that neither the Bukkit API nor the LuaLink API is guaranteed to be thread-safe.
```lua
-- Schedules asynchronous task to be run on the next tick.
scheduler:runAsync(handler: (BukkitRunnable) -> void): BukkitTask
-- Schedules asynchronous task to be run after {delay} ticks has passed.
scheduler:runDelayedAsync(handler: (BukkitRunnable) -> void, delay: number): BukkitTask
-- Schedules task to be run after {delay} ticks has passed, and repeated every {period} ticks.
scheduler:runRepeatingAsync(handler: (BukkitRunnable) -> void, delay: number, period: number): BukkitTask
```
