---
order: 92
icon: zap
---
# Auto Completion & Intellisense

<details>
<summary><strong>VSCode / VSCodium Setup</strong></summary>

If you want auto completion and intellisense for LuaLink scripts in VSCode (or VSCodium), follow these simple steps:

### 1. Install the Lua Extension

- Install the **sumneko Lua** extension:
  - [VSCode Marketplace](https://marketplace.visualstudio.com/items?itemName=sumneko.lua)
  - [Open VSX](https://open-vsx.org/extension/sumneko/lua)

### 2. Get the LuaLink LLS Addon

- Clone (recommended) or download [LuaLink/lualink-lls-addon](https://github.com/LuaLink/lualink-lls-addon)
- Cloning is recommended so you can update it easily:
  ```bash
  git clone https://github.com/LuaLink/lualink-lls-addon
  ```

### 3. Configure the Extension

- Open the settings for the Lua extension.
- Add a new entry to `Lua.workspace.library` and enter the path to your `lualink-lls-addon` folder.
- Set `Lua.runtime.plugin` to `lualink-lls-addon/plugin.lua`.
  - This setting requires editing the `settings.json` for the extension directly.

#### Note

It *should* be possible to just add the `lualink-lls-addon` folder to `Lua.workspace.userThirdParty` and have the plugin load only for LuaLink scripts, but in testing this didn't work. If you figure it out, please open an issue or join our Discord!

### Done!

If you did everything right, you should now get auto completion and intellisense for LuaLink in your Lua files. This should make developing scripts much easier!

</details>

<!-- Add more IDE instructions below as needed -->
