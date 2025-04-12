---
icon: package-dependencies
order: 97
---

# Dependencies
LuaLink provides a way to access and use plugins' APIs in your scripts. This feature is very powerful and makes it easy to integrate scripts with other plugins. It must be noted this has not been thoroughly tested yet and some issues may arise. Please be cautious when using this feature.

!!! warning EXPERIMENTAL
Current implementation, despite being relatively simple and fully functional, is still marked as experimental.
We may introuduce breaking changes to the way dependencies are declared and exposed to scripts.
!!!

<br />

<!--
## Declaring Dependencies
To declare a dependency, you must create an `init.lua` file in your script's folder. In this example we will use **[PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.19978/)**.

```lua /plugins/LuaLink/scripts/example_script/init.lua
depends {
    "PlaceholderAPI"
}
```

**Why is that important?** Declaring dependency will ensure that script will not be loaded if **PlaceholderAPI** plugin is missing.
-->

## Using Dependencies
Importing any class that belongs to an installed plugin should work out of the box. In this example we will use **[PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.19978/)**, a plugin you should be already familiar with.

Assuming the plugin is **installed** and **enabled** on the server, we should be able to call its API like any other function.
```lua /plugins/LuaLink/scripts/example_script/main.lua
local PlaceholderAPI = import("me.clip.placeholderapi.PlaceholderAPI")

script.logger:info(PlaceholderAPI:setPlaceholders(nil, "Server is running %server_variant% %server_version_full%"))
```
```log Console Output
[00:00:00 INFO]: [LuaLink/example_script] Server is running Paper 1.21.4-224
```
That's it. As mentioned earlier, current implementation is really simple and should just work.
