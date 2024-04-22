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

> [!TIP]
> Setting up commands will require you at the very least beginner level knowledge of Roblox LUA scripting.

In the *Commands* module, you can setup whatever commands you want! The functions' returned arguments are "args" & "API", args referencing to inputted arguments (e.g. "message"), and API referencing the RCC API, which you can use for various custom functions:
```lua
{
	["log [message]"] = {
		Description = "Logs a message!",
		Function = function(args, API)
			local message = args.message
			print("This is a message sent using the log command: " ..message)
		end,
	},
	["kick [player] [reason]"] = {
		Description = "Kicks out a player from the server with a reason",
		Function = function(args, API)
			local player = API.GetPlayerFromInput(args.player, true)
			local reason = args.reason or "No reason provided"
			
			API.FunctionPlayer(player, function(plyr)
				plyr:Kick(reason)
			end)
		end,
	},
}
```
