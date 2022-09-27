## Known issues and ToDo list
• None  


## Blizzard issues
• Heal Prediction API only works on direct heals, which means HoTs are broken  
• See https://github.com/Stanzilla/WoWUIBugs/issues/163  


## General Questions

**Can I use my ElvUI profile for all WoW versions ?**  
Yes. Just use the export & import functions in the Profiles section.  
Note: Don't forget to export the private tab under "Choose What To Export" aswell.  


## Chat questions

**How can I add more chat tabs ?**  
Rightclick your "General" chat tab -> Create New Window -> Name -> Accept  

**Can I get more chat windows attached to the right panel?**  
No, you can only have one dock. Blizzard doesn't support 2 docks.  
You can only use 1 tab on the 2nd dock.  

**Chat issues? Editbox bugged? Colors bugged? Do the following:**  
Open the ElvUI options and click on "Install" at the bottom.  
Skip all steps except (2) CVars and (3) Chat.  
Skip to the end and click "Finished"  
Chat Addon conflicts: Prat, Leatrix Combat Log Hide, Chatter, Glass  


## TBC specific Questions

**How can I see the happiness of my pet on my hunter?**  
Use either [happiness:full] or [happiness:icon] or [happiness:discord] as a custom tag  
Set it up here: /ec • UnitFrames • Pet • Custom Texts • Create Custom Text • Type "Happiness Pet" • Add one of the tags in the "Text Format" field.  

**How do I display numbers other than percentages on mobs?**  
Go to UnitFrames • Target • Health and replace your "Text Format" with [health:current]  
You can do the same for enemy NPC nameplates: NamePlates •  Enemy NPC •  Health •  "Text Format": [health:current]  

**Is there a built-in weapon swing timer or enemy swing timer in ElvUI?**  
No, we suggest to use a simple progress bar WeakAura or a lightweight AddOn for this feature.  


## UnitFrame Questions

**What are those little squares on my UnitFrames?**  
BuffIndicators for your class buffs, hots and shields. You can edit them here:  
Filters -> Select Filter -> Aura Indicator(Class) -> Select Spell  

**How can I disable / enable text (durations) on my Buff Indicators ?**  
Filters -> Select Filter -> Aura Indicator(Class) -> Select Spell -> Spell Name -> Display Text  

**How can I display all Buffs/Debuffs on my frames ?**  
UnitFrames -> Unit -> Buffs/Debuffs -> Filters -> Min/Maximum Duration -> 0  
UnitFrames -> Unit -> Buffs/Debuffs -> Filter Priority  
If you want to see all Buffs/Debuffs use the following Filter Priority  
1) Blacklist 2) Personal 3) NonPersonal  
How to set up Filters (Guide): https://www.tukui.org/forum/viewtopic.php?f=5&t=2  

**How can I display energy ticks and mp5 ticks?**  
Enable UnitFrames • Individual Units • Player • Power • Energy/Mana Regen Tick  


## NamePlate Questions

**How can I increase my nameplate distance in TBC?**  
NamePlates -> General -> Load Distance (41 yards is max for TBC)  

**I have only default Blizzard nameplates for friendly units in instances, any fix?**  
Blizzard controls friendly nameplates in Dungeons and Raids. Addons can't modify them.  

**My non-target nameplates are faded or don't show at all, any fix?**  
Step 1) NamePlates -> General Options -> Reset CVars  
Step 2) NamePlates -> Style Filter -> Select Filter -> (1) ElvUI_NonTarget -> Disable  