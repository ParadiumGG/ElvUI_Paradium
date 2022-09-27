## ElvUI Plugin Installer Framework

## Download

[MyPluginName.zip](https://github.com/Repooc/ElvUI-Templates/releases/download/1.0/MyPluginName.zip)

If you have questions or comments about this framework then feel free to post them in the offtopic section of our Discord.  

You can see the actual code and guidelines on how to use it below.  

## MyPluginName.toc File

The .toc file tells the WoW client about your addon, and tells it which files you would like it to load.  

```Lua
## Interface: 90105
## Author: YourName
## Version: 0.1
## Title: |cff1784d1ElvUI|r |cff00b3ffMyPluginName|r
## Notes: ElvUI Plugin Framework.
## RequiredDeps: ElvUI

ElvUI_PluginFramework.lua
```

## ElvUI_PluginFramework.lua file

The ElvUI_PluginFramework.lua file is where the actual framework code is kept.  

```Lua
--[[
	This is a framework showing how to create a plugin for ElvUI.
	It creates some default options and inserts a GUI table to the ElvUI Config.
	If you have questions then ask in the Tukui lua section: https://www.tukui.org/forum/viewforum.php?f=10
]]

local E, L, V, P, G = unpack(ElvUI); --Import: Engine, Locales, PrivateDB, ProfileDB, GlobalDB
local MyPlugin = E:NewModule('MyPluginName', 'AceHook-3.0', 'AceEvent-3.0', 'AceTimer-3.0'); --Create a plugin within ElvUI and adopt AceHook-3.0, AceEvent-3.0 and AceTimer-3.0. We can make use of these later.
local EP = LibStub("LibElvUIPlugin-1.0") --We can use this to automatically insert our GUI tables when ElvUI_Config is loaded.
local addonName, addonTable = ... --See http://www.wowinterface.com/forums/showthread.php?t=51502&p=304704&postcount=2

--Default options
P["MyPlugin"] = {
	["SomeToggleOption"] = true,
	["SomeRangeOption"] = 5,
}

--Function we can call when a setting changes.
--In this case it just checks if "SomeToggleOption" is enabled. If it is it prints the value of "SomeRangeOption", otherwise it tells you that "SomeToggleOption" is disabled.
function MyPlugin:Update()
	local enabled = E.db.MyPlugin.SomeToggleOption
	local range = E.db.MyPlugin.SomeRangeOption

	if enabled then
		print(range)
	else
		print("SomeToggleOption is disabled")
	end
end

--This function inserts our GUI table into the ElvUI Config. You can read about AceConfig here: http://www.wowace.com/addons/ace3/pages/ace-config-3-0-options-tables/
function MyPlugin:InsertOptions()
	E.Options.args.MyPlugin = {
		order = 100,
		type = "group",
		name = "MyPlugin",
		args = {
			SomeToggleOption = {
				order = 1,
				type = "toggle",
				name = "MyToggle",
				get = function(info)
					return E.db.MyPlugin.SomeToggleOption
				end,
				set = function(info, value)
					E.db.MyPlugin.SomeToggleOption = value
					MyPlugin:Update() --We changed a setting, call our Update function
				end,
			},
			SomeRangeOption = {
				order = 1,
				type = "range",
				name = "MyRange",
				min = 0,
				max = 10,
				step = 1,
				get = function(info)
					return E.db.MyPlugin.SomeRangeOption
				end,
				set = function(info, value)
					E.db.MyPlugin.SomeRangeOption = value
					MyPlugin:Update() --We changed a setting, call our Update function
				end,
			},
		},
	}
end

function MyPlugin:Initialize()
	--Register plugin so options are properly inserted when config is loaded
	EP:RegisterPlugin(addonName, MyPlugin.InsertOptions)
end

E:RegisterModule(MyPlugin:GetName()) --Register the module with ElvUI. ElvUI will now call MyPlugin:Initialize() when ElvUI is ready to load our plugin.
```

## How to properly use the framework as a skeleton for your own plugin:

You should change "MyPluginName" to something unique, perhaps incorporating your username or using a name that describes what the plugin is meant to do. Example: "BlazePlugin".  
Changing the title in the .toc file is optional, but you should always make sure you use a unique name when you create a module in ElvUI:  

```Lua
local MyPlugin = E:NewModule("BlazePlugin", "AceHook-3.0", "AceEvent-3.0", "AceTimer-3.0");
```

You should change the default options table. Replace "MyPlugin" with a unique name, perhaps the same name you used in step 1.  
Add the options you need to this table. You can always come back and add/remove options again later. Example:  

```Lua
--Default options
P["BlazePlugin"] = {
	["SomeToggleOption"] = true,
	["SomeRangeOption"] = 5,
}
```

When you change the default options table name, you need to update the rest of your code to reflect this change.  
Any lines in the code where you see "E.db.MyPlugin" needs to be updated to use the name you chose in step 2 (without quotes). For example:  

```Lua
E.db.BlazePlugin
```

In the "MyPlugin:InsertOptions()" function, you should change the table structure so that your GUI table uses a unique table key. Example:  

```Lua
E.Options.args.BlazePlugin = {
```