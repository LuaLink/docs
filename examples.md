---
icon: play
order: 93
---
# Examples
In this section you can find some example scripts written with LuaLink. Want to see your script here? **[Submit a PR](https://github.com/LuaLink/docs/pulls)** and we'll consider adding it to the list. 

<br />

## :icon-flame: Ragemode
Basic **One In The Chamber** (OIC) like gamemode, inspired by [Freggy's version](https://github.com/freggy/ragemode-lua) for LuaLink v1.

{.compact}
| Notes |
| ----- |
| 1. This script assumes that you are using the map **hijacked**. This map can be found in [Freggy's original repository](https://github.com/freggy/ragemode-lua). |

[!file](examples/ragemode.lua)
==- :icon-code: &ensp; Code
:::code source="examples/ragemode.lua":::
==-

<br />

## :icon-tools: Gamemode Commands
A basic script that provides shorthand commands for changing gamemodes.

{.compact}
| Command          | Description                | Permission                                     |
| ---------------- | -------------------------- | ---------------------------------------------- |
| `/gma [player]`  | Set game mode to Adventure | `minecraft.command.gamemode.adventure[.other]` | 
| `/gmsp [player]` | Set game mode to Spectator | `minecraft.command.gamemode.spectator[.other]` |
| `/gms [player]`  | Set game mode to Survival  | `minecraft.command.gamemode.survival[.other]`  |
| `/gmc [player]`  | Set game mode to Creative  | `minecraft.command.gamemode.creative[.other]`  |

{.compact}
| Notes |
| ----- |
| 1. The `[player]` argument is optional. If omitted, the command affects the sender. |
| 2. To change another player's gamemode, the sender must have the base permission plus `.other`. |
| 3. You can use `@a` as the player argument to affect all players. This also requires the `.other` permission extension.  |

[!file](examples/gamemode_commands.lua)

==- :icon-code: &ensp; Code
:::code source="examples/gamemode_commands.lua":::
==-
