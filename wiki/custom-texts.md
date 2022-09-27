## What are tags?
Sometimes you will want certain information on your UnitFrames.  
Some people would like to see what group they are in, how much health they have left as a percent or an abbreviated value.  
Tags will allow you to add this information and more to your UnitFrames.  

Elv has gone to great lengths to make sure you are covered when it comes to customizing your UnitFrames to be exactly how you want them.  
This comes with somewhat of a price tag (pun intented). This guide provides an outline that should get you where you want to go.  

## Config tabs
There are three important places in the ElvUI Config that you should be aware about:  
`Text Format` - This is where we will place our tags.  
`Custom Texts` - This will allow you to create new element to add custom text to your frame.  
`Element Selection` - You can use this tabs to select different elements to edit.  

## Step 1 - Choosing a UnitFrame
All of ElvUI UnitFrames support custom tags. Here is a compiled list of the frames ElvUI has:  
`Player` Frame  
`Target` Frame (**TargetTarget** Frame, **TargetTargetTarget** Frame)  
`Focus` Frame (**FocusTarget** Frame)  
`Pet`  Frame (**PetTarget** Frame)  
`Arena` Frames  
`Boss` Frames  
`Assist` Frames (**Tank** Frames)  
`Party` Frames (**Raid**, **Raid-40**, and **Raid Pet** Frames)  

## Step 2 - Creating a New Element

![Image 1](http://i.imgur.com/6xM4wEA.png "Image 1")  

Creating a new element with a unique and descriptive name.  

Before you create a custom tag, you might want to create an element to house it.  
An element is like a group of tags. It can have multiple tags in it, but when you move group, all the tags move together.  
In the example above, we wrote a unique and descriptive name in the Custom Text box which will help keep track of tags.  
There is no strict limitation on how many elements each UnitFrame can have.  

## Step 3 - Adding a Tag to an Element

![Image 2](http://i.imgur.com/kOfyNtR.png "Image 2")  

We can either add a tag to our new element or...  

![Image 3](http://i.imgur.com/F5QtNUj.png "Image 3")  

... we can change an element that is already in there!  

After creating or selecting an element, you can then adjust the tag using the Text Format box.  
This text will get parsed by ElvUI and then added to the UnitFrame.  
Here is an example of what you can do with an element:  

Text Format (Before the Parser):  
`[name] - ([level]) | HP: [health:current]`  

UnitFrame (After the Parser):  
`Dandruff - (90) | HP: 768.4K`  

Notice how only the square brackets are removed by the parser.  
This means that you can format your text however you like, with the exception of using square brackets.  
At the time of writing this guide, there are no ways to use square brackets in your text.  

Most of the tags which will be described below, are simple to use as they can be in any order.  
Color related tags require another tag to modify.  
In the example below, I use "namecolor" which will color the following text the color of the unit's class (a shaman).  
Notice how you can use ANY color tag with any other tag.  

Text Format (Before the Parser):  
`[namecolor][name] - HP: [namecolor][health:current]`  

UnitFrame (After the Parser):  
`Dandruff - HP: 768.4K`  

After you have finished adding the tags to the element, you can then adjust the position and other settings.  
In most cases, creating your own element and hiding the original will allow you to customize the custom text even further.  
For example, the Name element doesn't let you change the Font Outline.  
You can hide the original element by simply erasing the Text Format box.  

Thanks for reading this guide and I hope that it helped you out!  
A special thank you to Repooc, Elv, Edoc and Luckyone for their contribution to this guide.  