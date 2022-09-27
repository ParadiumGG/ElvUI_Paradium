## ElvUI Layout Installer Framework

## Information and Download

This is a framework you can use if you want to create an installer for one or more of your layouts.  
While you can always choose to simply export your profile and other settings, and then share those exports, a dedicated installer might be ideal if you have a lot of layouts you want to provide easy access to.  
I will explain what steps you need to take, and what code you need to fill in or replace.  

If you don't need help, or if you just want to get your hands on the framework to look at the code before you go any further, then you can grab the addon template here:  

[MyLayoutInstallerName.zip](https://github.com/Repooc/ElvUI-Templates/releases/download/1.0/MyLayoutInstallerName.zip)  

---

## Step by Step

Here I will try to guide you through all the steps that are necessary in order to create your own installer based on this framework.  

1. First you should download the framework addon at the top of this post if you have not done so already. Extract the archive on your Desktop for easy access to it.  
2. The next thing you want to do is to rename the addon. If everyone decided to keep the default name "ElvUI_LayoutInstaller" then the users would be unable to use multiple custom installers from different people. So right-click the extracted folder "ElvUI_LayoutInstaller" and click "Rename". Then choose a unique name for your layout installer. If it was me then I could perhaps use "ElvUI_BlazeflackLayouts".  
3. Now that we have renamed the addon folder, we also need to rename one of the files within the folder. So open the folder you just renamed and find the "ElvUI_LayoutInstaller.toc" file. Right-click it and click "Rename", then give it the same name as the folder you just renamed and keep the .toc extension (may not be visible to you).  
4. The next thing you want to do is open the Code.lua file in a text editor (I highly recommend to not use the default Notepad. Get a good text editor like Notepad++ which is free). On line 15 of the file you should replace "PUT_YOUR_UNIQUE_NAME_HERE" with a unique name for your layout plugin. If it was me then perhaps it could be "Blazeflack Layouts".  
5. Now you want to export your layout from ElvUI so it can be added to your installer. Log in on a character and go to the Profiles section of the ingame config, then click "Export Profile". Choose the profile (or private settings) you want to export, and then make sure to change the export format to "Plugin" before clicking the "Export Now" button. Many lines of text will be displayed in the text field, which you need to copy and then paste into your installer code. Mark all the text by pressing Ctrl+A and then copy it by pressing Ctrl+C. Go back to your Code.lua file in your text editor and look for the line that says "--LAYOUT GOES HERE" (on line 32). Put your cursor on the line below it (line 33) and then paste the exported text by pressing Ctrl+V. Now save the Code.lua file by pressing Ctrl+S (or do it through File -> Save).  
6. For the simple use of this framework that is all you have to do. Your installer is now ready to be used by yourself or others. Before distributing it to others I highly recommend testing it yourself to make sure it works as intended. Install the addon by moving/copying it to your /World of Warcraft/Interface/AddOns/ folder.  
7. For the more advanced users there are areas in the code you may want to look at. For example you could provide multiple layouts, or layout variations based on role. You could also provide a custom logo you want displayed in the installer frame, or add more steps to the installer in order to handle setup of other things (CVars, WoW chat settings etc.). You can also modify the text that is displayed on each page of the installer.  


## TLDR

Download and extract framework addon.  
Rename addon folder along with the .toc file (names should be identical and a unique name).  
Open Code.lua and replace "PUT_YOUR_UNIQUE_NAME_HERE" with your own unique name for your plugin.  
Export your chosen profile and/or private settings and choose "Plugin" as export format.  
Place the exported text below the "--LAYOUT GOES HERE" line.  
Install the addon and test it, or try to add more steps to the installer or modify existing steps if you are an advanced user.  

## Errors. I Need Help

If you experience errors after performing the steps outlined above, or if you need help modifying the framework further, then please post in the offtopic section of our Discord.  
Make sure you include the entire error text you get (if any) and/or explain in detail what you need help to accomplish.  

## MyLayoutInstallerName.toc File

If you just want to see what the code looks like without downloading the addon itself, then you can see the contents of the included files here.  

```Lua
## Interface: 80300
## Author: Blazeflack
## Version: 1.00
## Title: |cff1784d1ElvUI|r |cff4beb2cLayout Installer|r
## Notes: Contains layouts from SomePerson
## RequiredDeps: ElvUI
## DefaultState: enabled

Code.lua
```

## Code.lua File

```Lua
--Don't worry about this
local addon, ns = ...
local Version = GetAddOnMetadata(addon, "Version")

--Cache Lua / WoW API
local format = string.format
local GetCVarBool = GetCVarBool
local ReloadUI = ReloadUI
local StopMusic = StopMusic

-- These are things we do not cache
-- GLOBALS: PluginInstallStepComplete, PluginInstallFrame

--Change this line and use a unique name for your plugin.
local MyPluginName = "PUT_YOUR_UNIQUE_NAME_HERE"

--Create references to ElvUI internals
local E, L, V, P, G = unpack(ElvUI)

--Create reference to LibElvUIPlugin
local EP = LibStub("LibElvUIPlugin-1.0")

--Create a new ElvUI module so ElvUI can handle initialization when ready
local mod = E:NewModule(MyPluginName, "AceHook-3.0", "AceEvent-3.0", "AceTimer-3.0");

--This function will hold your layout settings
local function SetupLayout(layout)
	--[[
	--	PUT YOUR EXPORTED PROFILE/SETTINGS BELOW HERE
	--]]

	--LAYOUT GOES HERE



	--[[
		--If you want to modify the base layout according to
		-- certain conditions then this is how you could do it
		if layout == "tank" then
			--Make some changes to the layout posted above
		elseif layout == "dps" then
			--Make some other changes
		elseif layout == "healer" then
			--Make some different changes
		end
	--]]


	--[[
	--	This section at the bottom is just to update ElvUI and display a message
	--]]
	--Update ElvUI
	E:UpdateAll(true)
	--Show message about layout being set
	PluginInstallStepComplete.message = "Layout Set"
	PluginInstallStepComplete:Show()
end

--This function is executed when you press "Skip Process" or "Finished" in the installer.
local function InstallComplete()
	if GetCVarBool("Sound_EnableMusic") then
		StopMusic()
	end

	--Set a variable tracking the version of the addon when layout was installed
	E.db[MyPluginName].install_version = Version

	ReloadUI()
end

--This is the data we pass on to the ElvUI Plugin Installer.
--The Plugin Installer is reponsible for displaying the install guide for this layout.
local InstallerData = {
	Title = format("|cff4beb2c%s %s|r", MyPluginName, "Installation"),
	Name = MyPluginName,
	--tutorialImage = "Interface\\AddOns\\MyAddOn\\logo.tga", --If you have a logo you want to use, otherwise it uses the one from ElvUI
	Pages = {
		[1] = function()
			PluginInstallFrame.SubTitle:SetFormattedText("Welcome to the installation for %s.", MyPluginName)
			PluginInstallFrame.Desc1:SetText("This installation process will guide you through a few steps and apply settings to your current ElvUI profile. If you want to be able to go back to your original settings then create a new profile before going through this installation process.")
			PluginInstallFrame.Desc2:SetText("Please press the continue button if you wish to go through the installation process, otherwise click the 'Skip Process' button.")
			PluginInstallFrame.Option1:Show()
			PluginInstallFrame.Option1:SetScript("OnClick", InstallComplete)
			PluginInstallFrame.Option1:SetText("Skip Process")
		end,
		[2] = function()
			PluginInstallFrame.SubTitle:SetText("Layouts")
			PluginInstallFrame.Desc1:SetText("These are the layouts that are available. Please click a button below to apply the layout of your choosing.")
			PluginInstallFrame.Desc2:SetText("Importance: |cff07D400High|r")
			PluginInstallFrame.Option1:Show()
			PluginInstallFrame.Option1:SetScript("OnClick", function() SetupLayout("tank") end)
			PluginInstallFrame.Option1:SetText("Tank")
			PluginInstallFrame.Option2:Show()
			PluginInstallFrame.Option2:SetScript("OnClick", function() SetupLayout("healer") end)
			PluginInstallFrame.Option2:SetText("Healer")
			PluginInstallFrame.Option3:Show()
			PluginInstallFrame.Option3:SetScript("OnClick", function() SetupLayout("dps") end)
			PluginInstallFrame.Option3:SetText("DPS")
		end,
		[3] = function()
			PluginInstallFrame.SubTitle:SetText("Installation Complete")
			PluginInstallFrame.Desc1:SetText("You have completed the installation process.")
			PluginInstallFrame.Desc2:SetText("Please click the button below in order to finalize the process and automatically reload your UI.")
			PluginInstallFrame.Option1:Show()
			PluginInstallFrame.Option1:SetScript("OnClick", InstallComplete)
			PluginInstallFrame.Option1:SetText("Finished")
		end,
	},
	StepTitles = {
		[1] = "Welcome",
		[2] = "Layouts",
		[3] = "Installation Complete",
	},
	StepTitlesColor = {1, 1, 1},
	StepTitlesColorSelected = {0, 179/255, 1},
	StepTitleWidth = 200,
	StepTitleButtonWidth = 180,
	StepTitleTextJustification = "RIGHT",
}

--This function holds the options table which will be inserted into the ElvUI config
local function InsertOptions()
	E.Options.args.MyPluginName = {
		order = 100,
		type = "group",
		name = format("|cff4beb2c%s|r", MyPluginName),
		args = {
			header1 = {
				order = 1,
				type = "header",
				name = MyPluginName,
			},
			description1 = {
				order = 2,
				type = "description",
				name = format("%s is a layout for ElvUI.", MyPluginName),
			},
			spacer1 = {
				order = 3,
				type = "description",
				name = "\n\n\n",
			},
			header2 = {
				order = 4,
				type = "header",
				name = "Installation",
			},
			description2 = {
				order = 5,
				type = "description",
				name = "The installation guide should pop up automatically after you have completed the ElvUI installation. If you wish to re-run the installation process for this layout then please click the button below.",
			},
			spacer2 = {
				order = 6,
				type = "description",
				name = "",
			},
			install = {
				order = 7,
				type = "execute",
				name = "Install",
				desc = "Run the installation process.",
				func = function() E:GetModule("PluginInstaller"):Queue(InstallerData); E:ToggleOptionsUI(); end,
			},
		},
	}
end

--Create a unique table for our plugin
P[MyPluginName] = {}

--This function will handle initialization of the addon
function mod:Initialize()
	--Initiate installation process if ElvUI install is complete and our plugin install has not yet been run
	if E.private.install_complete and E.db[MyPluginName].install_version == nil then
		E:GetModule("PluginInstaller"):Queue(InstallerData)
	end
	
	--Insert our options table when ElvUI config is loaded
	EP:RegisterPlugin(addon, InsertOptions)
end

--Register module with callback so it gets initialized when ready
E:RegisterModule(mod:GetName())
```