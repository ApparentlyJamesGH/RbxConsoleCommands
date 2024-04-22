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

> [!NOTE]
> To view the full commands list, use `help`. And to view RCC internal commands, use `rcc help`. (All RCC commands must be called with the `rcc` prefix.)

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

## Extra Information
The error you get in the console after exeucting a command, `Incomplete statement: expected assignment or a function call`, is nothing you should worry about. This error only pops up because the Roblox console does not register the command name to be an actual command, because it is made programatically and is not an official Roblox command.
