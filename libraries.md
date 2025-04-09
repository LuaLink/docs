---
icon: package-dependents
order: 97
---

# Libraries
LuaLink provides a way to load external **Java** libraries for use in your scripts, as well as to define and/or use external **Lua** libraries.

<br />

## Lua Libraries
External Lua libraries can be added by copying files to the `/plugins/LuaLink/libs/` folder.

==- Example Lua Library
```lua **/plugins/LuaLink/libs/example_library/init.lua**
local Counter = {}
Counter.__index = Counter

-- Creates a new Counter instance.
function Counter.new()
    local self = setmetatable({}, Counter)
    self.count = 0
    return self
end

-- Increments the counter by one.
function Counter:increment()
    self.count = self.count + 1
end

-- Decrements the counter by one.
function Counter:decrement()
    self.count = self.count - 1
end

-- Returns the current counter value.
function Counter:get()
    return self.count
end

return Counter
```
==-

This is an example of a Counter class that allows you to increment, decrement, and get the current value of a counter.

Now, if you want to use this class in your script, you can import it using the `require` keyword.

```lua /plugins/LuaLink/scripts/example_script/init.lua
local Counter = require("example_library")

script:onLoad(function()
    -- Creating a new instance of the Counter class.
    local counter = Counter.new()
    -- Incrementing the counter three times.
    counter:increment()
    counter:increment()
    counter:increment()
    -- Printing current value of the counter to the console.
    script.logger.info(counter:get() .. " is the current value of the counter.")
end)
```

<br />

## Java Libraries
External Java/Kotlin libraries can be added by configuring the `/plugins/LuaLink/libraries.json` file. Dependencies will be downloaded and exposed to the scripting runtime after server restart.

### Configuration Example
```json5 /plugins/LuaLink/libraries.json
{
    // Repositories to be used for dependency resolution.
    "repositories": {
        // Repository definition using simple format.
        "MavenCentral": "https://repo.maven.apache.org/maven2/",
        // Repository definition with credentials authentication.
        "SomePrivateRepository": {
            "url": "https://repo.example.com/private",
            "username": "RepositoryUsername",
            "password": "SecretRepositoryPassword123"
        }
    },
    // Dependencies to be downloaded and exposed to the scripting runtime.
    // Entries must be specified using Maven coordinate format: groupId:artifactId:version
    "dependencies": [
        "com.github.stefvanschie.inventoryframework:IF:0.10.11"
    ]
}
```

In this example, we are adding stefvanschie's [IF](https://github.com/stefvanschie/IF) library of version `0.10.11` from [Maven Central](https://repo.maven.apache.org/maven2/) repository. You can also see how to add and authenticate with a private repository using credentials, which might be essential when working with closed-source projects or [GitHub Packages](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-apache-maven-registry).

After restarting the server, we should be able to import and access any class that belongs to specified library(-ies).

```lua /plugins/LuaLink/scripts/example_script/init.lua
-- TO-DO
```

<br />