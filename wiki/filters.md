## Filter Types

`Whitelists:` Personal, nonPersonal, Boss, CastByUnit, notCastByUnit, Dispellable (includes steal-able), CastByNPC, CastByPlayers  
`Blacklists:` blockNonPersonal, blockNoDuration, blockCastByPlayers  
A blacklist filter is only effective against filters that come after it in the priority list.  
It will not block anything from the filters before it.  

## Descriptions

`Boss:` Auras (debuffs only?) cast by a boss unit.  
`Personal:` Auras cast by yourself.  
`nonPersonal:` Auras cast by anyone other than yourself.  
`CastByUnit:` Auras cast by the unit of the unitframe or nameplate (so on target frame it only shows auras cast by the target unit).  
`notCastByUnit:` Auras cast by anyone other than the unit of the unitframe or nameplate.  
`Dispellable:` Auras you can either dispel or spellsteal.  
`CastByNPC:` Auras cast by any NPC.  
`CastByPlayers:` Auras cast by any player-controlled unit (so no NPCs).  
`blockCastByPlayers:` Blocks any aura that is cast by player-controlled units (so will only show auras cast by NPCs).  
`blockNoDuration:` Blocks any aura without a duration.  
`blockNonPersonal:` Blocks any aura that is not cast by yourself.  


## How Filters Work

If the Filter Priority list is empty, then all auras will be allowed through.  
As soon as you add a filter to the priority list then it will start by blocking all auras, and then only allow an aura through if it passes the filter condition, assuming the filter is a whitelist.  
If you have 2 filters in your priority list, a blacklist and a whitelist, and the blacklist has a higher priority (is listed before whitelist), then an aura will not be allowed if it is in the blacklist filter, even if it is also in the whitelist filter.  
If an aura is matched against a filter, then it will stop there and not try to match against any of the remaining filters.  
This gives you full control over what filters you consider the most important in any type of situation (raiding, pvp etc.).  


## Examples

**Show Everything**  
**Set "Max Duration" to 0**  
`Leave Priority List Empty`  
Alternative:  
`(1) Personal | (2) nonPersonal`  


**Block Blacklisted Auras, Show Everything Else**  
`(1) Blacklist| (2) Personal | (3) nonPersonal`  


**Block Auras Without Duration, Show Everything Else**  
`(1) blockNoDuration | (2) Personal | (3) nonPersonal`  


**Block Auras Without Duration, Block Blacklisted Auras, Show Everything Else**  
`(1) blockNoDuration | (2) Blacklist | (3) Personal | (4) nonPersonal`  


**Block Everything, Except Your Own Auras**  
`(1) Personal`  


**Block Everything, Except Whitelisted Auras**  
`(1) Whitelist`  


**Block Everything, Except Whitelisted Auras That Are Cast By Yourself** (custom whitelist filters can be used too)  
`(1) blockNonPersonal | (2) Whitelist`  