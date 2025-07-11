---
order: 91
icon: zap
---
# Auto Completion & IntelliSense
To enhance your development experience with LuaLink, it is recommended to set up auto completion with IntelliSense.

Getting this up and running is really simple. Choose your IDE and follow instructions below:

=== **Visual Studio Code** &ensp; | &ensp; **VSCodium**

<br>

#### 1. Install Lua Extension
Download and install **sumneko Lua** extension. You can do this manually, or use built-in extension manager if available.

{.list-icon}
- **Trusted Sources**
- [**:icon-link: VSCode Marketplace** (marketplace.visualstudio.com)](https://marketplace.visualstudio.com/items?itemName=sumneko.lua)
- [**:icon-link: Open VSX** (open-vsx.org)](https://open-vsx.org/extension/sumneko/lua)

---

#### 2. Get LuaLink LLS Addon
Clone or download [**our addon**](https://github.com/LuaLink/lualink-lls-addon). It contains Lua stubs for common Java and Bukkit types and enables auto-completion of class names.

Cloning is recommended so you can update it easily.
```bash
git clone https://github.com/LuaLink/lualink-lls-addon
```
Updating is as simple as executing `git pull` inside the cloned directory.

**Note**: Stubs are based on JDK 21 and latest Paper API snapshot. Repository is updated on daily basis so if recently added API is missing, just pull changes from remote or download and replace files manually.

---

#### 3. Configure Lua Extension
The last step is to configure **sumneko Lua** extension to make it recognize and index downloaded Lua stubs, and use our runtime plugin.

- Open the settings for the Lua extension.
- Add a new entry to `Lua.workspace.library` and enter the path to your `lualink-lls-addon` folder.
- Set `Lua.runtime.plugin` to `lualink-lls-addon/plugin.lua`.
  - This setting requires editing the `settings.json` for the extension directly.

**Note**: It *should* be possible to just add the `lualink-lls-addon` folder to `Lua.workspace.userThirdParty` and have the plugin load only for LuaLink scripts. We could never get this to work however. So if you figure it out - please [open a new issue](https://github.com/LuaLink/docs/issues) or [join our Discord](https://discord.gg/xYcjBKqkDz).

===

**Not working?** [Join our Discord server](https://discord.gg/xYcjBKqkDz) and ask for help. We will do our best to help you set it up.

<!-- Add more IDE instructions below as needed -->
