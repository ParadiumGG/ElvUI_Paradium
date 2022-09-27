## Step 1: System - Graphics - Raid and Battleground

First of all you want to enable the checkbox **"Enable Raid and Battleground Settings"** and then  
switch over to the tab **"Raid and Battleground"** to setup your graphics quality in instance content.  

Following with some recommendations and explanations. They will obviously not work for every system and setup.  

> General

* `Graphics Quality` can be **10**. It will automatically switch over to **Custom** in our process of tweaking.  
* `Texture Resolution` can be **High**. Performance impact is almost non-existent and your game will look better.  
* `Spell Density` should be **Essential**. Less effects on your screen. You will still see important effects like healing zones.  
* `Projected Textures` has to be **Enabled**. Otherwise you will miss important void zones and die to boss mechanics.  

> Environment

* `View Distance` does not exist in instances. You should set it to **1**.  
* `Environment Detail` does not exist in instances. You should set it to **1**.  
* `Ground Clutter` does not exist in instances. You should set it to **1**.  

> Effects

* `Shadow Quality` can be **Low**.  
* `Liquid Detail` can be **Low**.  
* `Particle Density` atleast **High**. Recommended **Ultra** if your System is good.  
* `SSAO`, `Depth Effects` and `Compute Effects` should be **Disabled**.  
* You want `Outline Mode` set to **High**.  

> Example screenshot

* This is the Raid and Battleground tab. Open world content is not affected by this.  

![Raid and Battleground](https://i.imgur.com/jYmPVEe.png "System -> Graphics -> Raid and Battleground")

> Anti-Aliasing

* Turn it off. In your Graphics tab top left. (Set to "None").  
* You will immediately see the difference if you look at player and NPC names.  

> Resolution Scale (Big FPS!)

* You can try a resolution scale lower than 100% combined with the next step. Example: 83%.  
* `Resample Quality` **FidelityFX Super Resolution 1.0** in the Advanced tab.  
* `Resample Sharpness` set it to 0.0 (right side of the page).  

> Console commands for Raid effects

* `/console RAIDWaterDetail 0` (Default is 0)  
* `/console RAIDweatherDensity 0` (Default is 3)  

## Step 2: Lua errors

Lua errors **will always** impact your performance. Even if you have them hidden.  

> Blizzard Console Variable

* Enable the error frame with the following chat command `/console scriptErrors 1`  
* Reload your UI with the following chat command `/reload`  

> BugSack and BugGrabber

* We recommend to download [BugSack](https://www.curseforge.com/wow/addons/bugsack) and [BugGrabber](https://www.curseforge.com/wow/addons/bug-grabber).  
* BugGrabber will catch all your Lua errors and consolidate them into a Minimap icon which you can open on click.  
* This is the best way to go through your errors and share them with AddOn authors so they can fix them.  

## Step 3: Optimizing in General

> Friendly NamePlates

* You don't want to enable Friendly NamePlates in Raids. Even in name-only mode with hidden health bars.  
* They have a major performance impact in situations where auras (Buffs and Debuffs) are applied to your Raid.  
* All the health events in the background will still fire and kill your FPS.  
* This is a Blizzard bug, because they just set the health bar alpha to 0 instead of fully deactivating them.  

> Profiling

* Profiling your CPU and Memory usage is nice, but it does impact your performance.  
* Make sure to disable it with the following chat command `/console scriptProfile 0` and then `/reload`  
* Make sure to disable addons like **AddOn CPU Usage** if you don't need them.  

## Step 4: Optimize your ElvUI

> General - Cosmetic

* Using **Thin Borders**, **UnitFrame Thin Borders** and **Nameplate Thin Borders** will improve your fps slightly.  

> ActionBars

* If you have active bars which you never really interact with, disable them. You can still use the hotkeys on it.  

> Cooldown Text

* We recommend to use the ElvUI Cooldown Text module instead of AddOns like OmniCC.
* Our module is optimized for ElvUI frames.  

> DataBars

* Disable bars if you don't need them. Completely disable Experience on max level.  
* Turn off threat if you don't care about it.  

> NamePlates

* Do not use **Portraits** or **Heal Prediction** for the best performance.  
* Clean up old **Style Filters** if you no longer use them.  

> Tooltip

* Disable **Target Info** and **Role** for the best performance.  
* Other informations are automatically hidden in combat and won't have any impact.  

> UnitFrames

* Disable **Smooth Bars** in the General tab of UnitFrames.  
* The bigger your **Filter Priority** for Buffs and Debuffs, the higher the performance impact. Try to optimize them.  
* Do not use 3D **Portraits**.  
* Do not use **Heal Prediction** for all frames if you are for example a DPS or Tank and don't need the information.  

## Bonus

**It is highly recommended to do a full reset of your World of Warcraft installation for each expansion release.**  

This is obviously something people don't like to do but a clean install will improve your stability and performance.  
Don't backup any files when doing this. Especially not the WTF or Interface folders. You want a full reset.  
You can export your profile strings, but you should not carry over old files to the new install.  
Your keybinds and actionbar spell placements will not reset. They are stored on Blizzards server.  

The best time to perform a full reset is between the Pre-Expansion patch and the full Expansion release.  

## Related Links

* [Troubleshooting and Testing](https://github.com/tukui-org/ElvUI/wiki/performance-troubleshooting)
