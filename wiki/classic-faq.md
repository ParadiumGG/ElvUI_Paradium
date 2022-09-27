## Known issues and ToDo list
• None  


## Blizzard issues
• Heal Prediction API only works on direct heals, which means HoTs are broken  
• See https://github.com/Stanzilla/WoWUIBugs/issues/163  


## General Questions

**Current version of ElvUI Classic?**  
You can check the latest version and read the changelog here: https://www.tukui.org/classic-addons.php?id=2  
Please check your version number on top of /ec or /estatus against the most recent version!  

**My ElvUI doesn't load / I can't open my ElvUI options / ElvUI broken after update**  
Don't install AddOns while WoW is running. WoW doesn't register addon changes until you exit the game and restart it.  
Check the capitalization of your ElvUI folders, case matters: "ElvUI" and "ElvUI_OptionsUI"  

**Can I use my retail profile in Classic?**  
Yes you can! Just export your retail profile ( /ec • Profiles • Export Profile • Export Now ) and import it  
in ElvUI Classic ( /ec • Profiles • Import Profile • Import Now ) and you are good to go.  


## Chat Questions

**How can I add more chat windows?**  
Rightclick your "General" tab • Create New Window • Set Name • Accept  

**Can I get more chat windows attached to the right panel?**  
No, you can only have one dock. Blizzard doesn't support 2 docks.  
You can only use 1 window on the 2nd dock.  

**Chat issues? Editbox bugged? Colors bugged? Try the following:**  
Open the ElvUI options, click on "Install" at the bottom.  
Skip all steps except (2) CVars and (3) Chat.  
Skip to the end and click "Finished"  
Chat Addon conflicts: Prat, Leatrix Combat Log Hide, Chatter, Glass  


## Classic Features

**How can I see the happiness of my pet on my hunter?**  
Use either [happiness:full] or [happiness:icon] or [happiness:discord] as a custom tag  
Set it up here: /ec • UnitFrames • Pet • Custom Texts • Create Custom Text • Type "Happiness Pet" • Add one of the tags in the "Text Format" field.  

**How do I display numbers other than percentages on mobs?**  
Go to UnitFrames • Target • Health and replace your "Text Format" with [health:current]  
You can do the same for enemy NPC nameplates: NamePlates •  Enemy NPC •  Health •  "Text Format": [health:current]  

**Is there a built-in weapon swing timer or enemy swing timer in ElvUI?**  
No, we suggest to use a simple progress bar WeakAura or a lightweight AddOn for this feature.  

**How do I use the abilities of a mindcontrolled enemy?**  
The mind control and possess bar is your pet bar. Make sure to enable it at ActionBars • Pet Bar  


## UnitFrame Questions

**What are those little squares on my UnitFrames?**  
BuffIndicators for your class buffs, hots and shields. You can edit them here:  
Filters • Select Filter • BuffIndicator • Select Spell  

**How can I disable / enable text (durations) on my Buff Indicators?**  
Filters • "Select Filter" • BuffIndicator • "Select Spell" • Spell Name & Rank • Display Text  

**I can't see most debuffs / buffs on my frames, how to show them again?**  
UnitFrames -> Unit -> Buffs/Debuffs -> Filters -> Min/Maximum Duration -> Set both to 0  
UnitFrames -> Unit -> Buffs/Debuffs -> Filter Priority  
If you want to see all Buffs/Debuffs use the following Filter Priority  
1: Blacklist 2: Personal 3: NonPersonal  
How to set up Filters (Guide): https://github.com/tukui-org/ElvUI/wiki/filters 

**How can I display energy ticks and mp5 ticks?**  
Enable UnitFrames • Individual Units • Player • Power • Energy/Mana Regen Tick  


## NamePlate Questions

**How can I increase my nameplate distance in Classic?**  
You can't increase it in Classic. Blizzard locked them to 20 yards max.  

**I have only default Blizzard nameplates for friendly units in instances, any fix for this?**  
Blizzard controls friendly nameplates in dungeons and raids. Addons can't touch them.  

**My non-target nameplates are faded or don't show at all, where can I edit that?**  
Step 1: NamePlates • General Options • Reset CVars  
Step 2: NamePlates • Style Filter • Select Filter • (1) ElvUI_NonTarget • Actions • Alpha • Set to -1  


## Style Filter Setup

**How to make a Style Filter for civilian NPCs:**  
- Create a new Style Filter at NamePlates • Style Filter • Name it Civilian  
- Triggers • Unit Conditions • Enable Unit is Civilian  
- Actions • Health • Enable Color Health and set a color for civilian NamePlates  