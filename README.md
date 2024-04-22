# RbxConsoleCommands (RCC)
RbxConsoleCommands are developer commands, made so game developers can execute specific functions easier and quicker.

> [!CAUTION]
> **THE SECURITY OF COMMAND EXECUTION HAS NOT YET BEEN VALIDATED AND SHOULD NOT BE USED AS A GO-TO DEVELOPER TOOL!**

| [Get Model on Roblox](https://create.roblox.com/store/asset/17256397886) |
| ------------- |

Made by [ApparentlyJames](https://apparentlyjames.carrd.co/)

## Basic Usage
In the *Settings* module, you can setup the options to however you want, it's mostly self explanitory:
```lua
{
	SeperateCommandCalls = print, -- Set to nil, print or warn
	AfterCallback = function(commandInfo, API)
		-- Can be used for command logs and stuff
		print("Command called!")
	end,
}
```
