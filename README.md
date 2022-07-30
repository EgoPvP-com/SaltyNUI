# SaltyNUI
Discourage Users without Temspeak running when using SaltyChat!


The goal of this simple Lua scirpt is to block Player from moving & display a black screen when your Server is using the SaltyChat System but the the Player isnt online on your Teamspeak Server similar to TokoVoip's one.

## What is Saltychat?
SaltyChat is an Open-Source Community Supported Proximity Chat system using a Teamspeak Server instead of the GTA-V Voice Chat. 
It offers many features besides the Proximity Chat like Radio Channels and Private Phone Calls.

[Download SaltyChat](https://github.com/saltminede/saltychat-fivem)


## Get the Script
You canget the script from out script-store [CLICK ME](https://shop.egorp.net/package/4668315)

## How to Install?
### Basic Installation
- Get the Script from our Store: [CLICK ME](https://shop.egorp.net/package/4668315)
- Rename the Downloaded Folder to "saltynui"
- Copy the Folder into your ressources/ folder
- Add `ensure saltynui` to your server.cfg and make sure the NUI is started AFTER SaltyChat.

On the Basic Installation SaltyNUI only gets triggered when u mute your Microphone. To get triggered when Player is in Wrong Server/Channel or isnt even Online you need the Advanced Installation!

## Advanced Installation
### For Saltychat 2.2.x  - LATEST

- Open the SaltyChat C# solution in VS
- Open SaltyClient/VoiceManager.cs
- Goto Line ~640 and add 
```c#
if (this.PlguinState == GameInstanceState.Ingame){
BaseScript.TriggerEvent("SaltyNUI:TsActive");
}else{
BaseScript.TriggerEvent("SaltyNUI:TsNotActive");
}
```
to the OnMessage Event (under case Command.InstanceState)
It should look somethings like [THIS](https://screens.egopvp.com/files/2021/04/02/devenv_e0uIMJJ1Mt.png) 

- Goto Line 500 and add `BaseScript.TriggerEvent("SaltyNUI:TsNotActive");` to the OnDisconnected Event (It should look like [THIS](https://screens.egopvp.com/files/2020/05/30/devenv_g5rbAJWpAH.png))
- !!IMPORTANT!! COMPILE SALTYCHAT AGAIN AND RE-UPLAOD IT!

These events gets triggered when Players close their Teamspeak Client and connect to a server / switch Channels

### For Saltychat 2.0.x - 2.1.2

- Open the SaltyChat C# solution in VS
- Open SaltyClient/VoiceManager.cs
- Goto Line ~564 and add 
```c#
if(instanceState.IsReady){
   BaseScript.TriggerEvent("SaltyNUI:TsActive");
 }else{
   BaseScript.TriggerEvent("SaltyNUI:TsNotActive");
 } 
```
to the OnMessage Event (under case Command.InstanceState)
It should look somethings like [THIS](https://screens.egopvp.com/files/2020/08/07/devenv_0dI2m50Rvj.png) 

- Goto Line 500 and add `BaseScript.TriggerEvent("SaltyNUI:TsNotActive");` to the OnDisconnected Event (It should look like [THIS](https://screens.egopvp.com/files/2020/05/30/devenv_g5rbAJWpAH.png))

- !!IMPORTANT!! COMPILE SALTYCHAT AGAIN AND RE-UPLAOD IT!

These events gets triggered when Players close their Teamspeak Client and connect to a server / switch Channels

### For Saltychat 1.x.x

- Open the SaltyChat C# solution in VS
- Open SaltyClient/VoiceManager.cs
- Goto Line ~560 and add 
```c#
if(pluginState.IsReady){
   BaseScript.TriggerEvent("SaltyNUI:TsActive");
 }else{
   BaseScript.TriggerEvent("SaltyNUI:TsNotActive");
 } 
```
to the OnMessage Event (under case Command.StateUpdate)
It should look somethings like [THIS](https://screens.egopvp.com/files/2020/05/30/devenv_58LaZ8WVeJ.png) 

- Goto Line 500 and add `BaseScript.TriggerEvent("SaltyNUI:TsNotActive");` to the OnDisconnected Event (It should look like [THIS](https://screens.egopvp.com/files/2020/05/30/devenv_g5rbAJWpAH.png))

- !!IMPORTANT!! COMPILE SALTYCHAT AGAIN AND RE-UPLAOD IT!

These events gets triggered when Players close their Teamspeak Client and connect to a server / switch Channels

## What if i want to Whitelist Swiss-Channels in SaltyNUI

### !!IMPORTANT!! If you have added every channel beside the "Join here to get moved into ingame channel" People **WILL** be able to Play on your Server by just joining your Teamspeak Server and sitting in **ANY** channel they like. Even if its not the "Ingame" channel thus defeting this script's purpose.
If you want to have People be able to go into Support & have them still able to play on the Server, just move the out of the "ingame" channel. Moving the player wont trigger saltynnui to be displayed. 

Also setting up every channel besides the "waiting" channel as a Swiss-Channel is **NOT** recommended!

- Instead of adding the above code to Line ~640 add this one:
```c#
if (this.PlguinState == GameInstanceState.Ingame || this.PlguinState == GameInstanceState.InSwissChannel){
BaseScript.TriggerEvent("SaltyNUI:TsActive");
}else{
BaseScript.TriggerEvent("SaltyNUI:TsNotActive");
}
```

## Other Scripts
We now offer Custom Script creations at our Store: [CLICK ME](https://shop.egorp.net/category/custom-development)

- [SaltyNUI](https://shop.egorp.net/package/4668315) - Discourage Users without Temspeak running when using SaltyChat!
- [erp_saltycircle](https://shop.egorp.net/package/4668429) - A basic Circle, visualizing your current voice range when using Saltychat

- [erp_weaponrange](https://shop.egorp.net/package/5167273) - Have people do some shooting excersise before gaining the Weapons License.
- [erp_towscript](https://shop.egorp.net/package/4668418) - Highly Customisable and top working Vehicle Towing Script for FiveM

- [erp_antifalldown](https://github.com/EgoPvP/erp_antifalldown) - Stop your Player from falling into the dark void.
- [erp_antiwhipping](https://github.com/EgoPvP/erp_antiwhipping) - Stop Players from hitting others when standing close.

- [erp_racing](https://shop.egorp.net/package/4666867) - Battle your Friends in epic 1 vs 1 races across LosSantos!

- [sitdown](https://shop.egorp.net/package/4668426) - Sitting made easy!

## Support
If you need any kind of Support, feel free to open an Issue.

### A lot of u guys seem to have problems READING the Readme. Make shure u read it carefully and didnt miss anything and added the Event-Triggers like you should. I dont Provide a screenshot for you to not use it. Its supposed to be a helping thing.

### Be aware that the Official SaltyChat Devs wont give you support of any kind for 3rd party ressources and only reffer to asking me.

### Make sure, u provide ur SaltyChat version and a Screenshot of the Code that you have added so i can do some proper bugfixxing!

Otherwise you can Contact me here:
[Discord](https://discord.gg/qRc5Hbb)

## Script store

If you are looking for more Scripts, check out our Custom Script Store: <br>
[shop.egorp.net](https://shop.egorp.net/)

## License

SaltyNUI - Discourage Users without Temspeak running when using SaltyChat!

Copyright (C) 2020 - [EgoPvP.com](https://egopvp.com)

