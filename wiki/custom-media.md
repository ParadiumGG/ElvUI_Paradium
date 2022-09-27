## Adding Fonts, Textures and Sounds through SharedMedia

## First Things First

Download and install SharedMedia ( https://www.curseforge.com/wow/addons/sharedmedia )  

## Automatic Method (For Windows)

Open the SharedMedia folder (**World of Warcraft / Interface / Addons / SharedMedia**) and rename MyMedia.bat.txt to MyMedia.bat make sure you have Windows set to show all file extensions.  
Run MyMedia.bat to create the necessary folders  
Put your media files into the sub-folders found at: **World of Warcraft / Interface / Addons / SharedMedia_MyMedia**  
Run MyMedia.bat again to create the MyMedia.lua file, which contains the necessary code to register your files  
**Optional:** If you want to edit the in-game name of your newly added media, then open the MyMedia.lua file and change the text in the 2nd set of quotes (see image 5)  

## Automatic Method: Images

![Image 1](https://i.imgur.com/nfHBxUJ.png "Image 1")

## Manual Method

Create a folder named "SharedMedia_MyMedia" inside your addons folder (World of Warcraft / Interface / AddOns / SharedMedia_MyMedia)  
Create subfolders named "background", "border", "font", "sound" and "statusbar"  
Place your media files into the corresponding folders  
Create a new text file called "SharedMedia_MyMedia.toc".
Open the file and insert the following code:

```
## Interface: 90200
## Title: SharedMedia_MyMedia
## Dependencies: SharedMedia
MyMedia.lua
```

Create a new text file called "MyMedia.lua", then remove the .txt from the name so the extension becomes .lua.  
Open the file and insert the following code:  

```Lua
----------------------------------------------------------------------------
-- Copy this section of the file to a file called MyMedia.lua, and enter
-- your medias information, using the examples shown below.
----------------------------------------------------------------------------

local LSM = LibStub("LibSharedMedia-3.0")

-- START of the section that you should be editing
--
--    NB: any line beginning with "--" is ignored - so the lines
--    below are just comments!
--

--background:

--border:

--font:

--sound:

--statusbar:

-- END of the section that you should be editing
```

Use the examples below to add information about your newly added media.  
You should only need to change anything between the lines marked "START" and "END".  
Each item of media that you want to add should have its own line that uses the relevant example as a template.  
To add details about more than one item, just add another line to that section, changing the specific details (eg: font name and path).  

## Manual Method: Examples

```Lua
LSM:Register("background", "my background's name", [[Interface\AddOns\SharedMedia_MyMedia\background\mybackground.tga]])
LSM:Register("border", "my border's name", [[Interface\AddOns\SharedMedia_MyMedia files\myborder.tga]])
LSM:Register("font", "my font's name", [[Interface\AddOns\SharedMedia_MyMedia\font\myfont.ttf]])
LSM:Register("font", "my friend's font", [[Interface\AddOns\SharedMedia_MyMedia\font\friendsfont.ttf]])
LSM:Register("sound", "my sound's name", [[Interface\AddOns\SharedMedia_MyMedia\sound\mysound.mp3]])
LSM:Register("statusbar", "my statusbar texture's name", [[Interface\Addons\SharedMedia_MyMedia\statusbar\mytexture.tga]])
```