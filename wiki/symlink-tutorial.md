How you use your Git Folders (if you are using a Git Client, like SmartGit & GitKraken etc) in your WoW installation.  

I keep this clean and simple and i assume you already use Git and know where your Git folders  
and `World of Warcraft \ _retail_ \ Interface \ AddOns` folder are. I will take ElvUI as an example.  

**The big advantage is that you don't need to copy your folders now everytime you pull the new changes.**

Delete your existing "ElvUI" & "ElvUI_OptionsUI" folders from your World of Warcraft folder.  
Open the windows command prompt as admin. Type in the windows search: **CMD**  

![Image 1](https://i.imgur.com/LGiZBn4.png "Image 1")

In the Command Prompt now must use the "mklink /D" command (Symlink)  
In the first part, we need to tell the link where you want your folder, so it should be  
the `World of Warcraft \ _retail_ \ Interface \ AddOns` folder.  

![Image 2](https://i.imgur.com/WVuqxg9.png "Image 2")

After this, we must tell the link, the path to our existing Git folder:  

![Image 3](https://i.imgur.com/M8n1rBi.png "Image 3")

The whole link now should looks like this:  

![Image 4](https://i.imgur.com/Av9kOk6.png "Image 4")

If you hit enter, it will create a new folder called "ElvUI" in your  
`World of Warcraft \ _retail_ \ Interface \ AddOns` folder and use the existing Git folder.  

![Image 5](https://i.imgur.com/D5lrmQ3.png "Image 5")

Repeat the steps with the folder "ElvUI_OptionsUI":  

![Image 6](https://i.imgur.com/xpCzAZY.png "Image 6")