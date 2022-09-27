# ElvUI performance troubleshooting guide

> **Preparation**
1. Download and install the latest ElvUI build and the ElvUI_CPU plugin (for help see our Install guide in the sidebar)  
2. Enable Blizzards CPU profiling with the following chat command `/console scriptProfile 1`  
3. Start the ElvUI debugging mode using the following chat command `/edebug on`   
4. Open up the profiling window using the following chat command `/ecpu`  
> **Data collection**
1. Start collecting data by clicking on ![Start](https://i.imgur.com/JmgYwrX.png "Start") before pulling the boss encounter  
2. Finish the boss encounter and stop the data collection by clicking on ![Stop](https://i.imgur.com/OhqonOf.png "Stop")  
3. If you want to profile multiple encounters make sure to reset the data in between pulls using the ![Reset](https://i.imgur.com/LSiR6NP.png "Reset") button  
> **Share results**
1. Upload 3 screenshots of your results in our Discord channel #elvui-performance  
2. One of them sorted by `calls/sec`  
3. The other one sorted by `time/call`  
4. And one of the `/estatus` panel  
> **Finish debugging**
1. To leave the debug mode, cleanup your cache and re-enable your other AddOns type in chat `/edebug off`  

# Links

1. [Latest ElvUI Build](https://www.tukui.org/download.php?ui=elvui)  
2. [ElvUI CPU plugin](https://github.com/Resike/ElvUI_CPU/archive/refs/heads/master.zip)  
3. [Discord invite link](https://discord.gg/xFWcfgE)