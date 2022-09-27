The posting of errors seems to be the hardest part on the forums or Discord.  
So let's cover if it should be considered a error or just ignore it.  

If the message begins with **ADDON_ACTION_BLOCKED** it is a Taint which never blames  
the right AddOn and is generally dismissive as an error.  
These are the hardest ones to diagnose because you guys have about 100 AddOns enabled  
and then it says ElvUI is tainting it.. when in fact it could be any AddOn.  

You need to disable Taint Logging. /ec - General - Log Taints.  
If that is disabled.. you need to disable it in Swatter or BugGrabber.  

If the messages say **Error Loading**.. You updated while WoW was open OR It's an error on the AddOn side.  
These never need posted. Restart WoW. If it still pops up then go post on that AddOn's page.  

The remaining error is a lua error and if it doesn't say ElvUI then don't post it.  

## ElvUI Lua Error

```Lua
Message: Interface\AddOns\ElvUI\Modules\chat\Chat.lua:1147: attempt to index local 'accountInfo' (a nil value)
Time: Thu Nov  7 21:05:20 2019
Stack: Interface\AddOns\ElvUI\Modules\chat\Chat.lua:1147: attempt to index local 'accountInfo' (a nil value)
```

## AddOn Lua Error

```Lua
Message: Interface\AddOns\AddOnSkins\Core\Config.lua:5: attempt to index global 'Tukui' (a nil value)
Time: Wed Oct 30 00:05:47 2019
Count: 1
Stack: Interface\AddOns\AddOnSkins\Core\Config.lua:5: attempt to index global 'Tukui' (a nil value)
Interface\AddOns\AddOnSkins\Core\Config.lua:5: in main chunk
```