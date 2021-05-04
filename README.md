# Dungeon Siege 2 Troubleshooting Guide

## Table of Contents

* [1.0 Glossary](#glossary)
* [2.0 Guides](#guides)
   * [2.1 Add the game on GameRanger](#add-the-game-on-gameranger)
   * [2.2 Change the FOV](#change-the-fov)
   * [2.3 Enable BW + Extras](#enable-bw--extras)
   * [2.4 Increase shadow resolution](#increase-shadow-resolution)
   * [2.5 Increase UI size](#increase-ui-size)
   * [2.6 Play borderless fullscreen](#play-borderless-fullscreen)
   * [2.7 Play online](#play-online)
   * [2.8 Play windowed](#play-windowed)
* [3.0 Issues fixed](#issues-fixed)
   * [3.1 Camera spinning too fast](#camera-spinning-too-fast)
   * [3.2 Crash/exception](#crashexception)
   * [3.3 Join button doesn't work](#join-button-doesnt-work)
   * [3.4 LAN games are not visible](#lan-games-are-not-visible)
   * [3.5 Missing/corrupted DLLs](#missingcorrupted-dlls)
   * [3.6 Mouse cursor is missing](#mouse-cursor-is-missing)
   * [3.7 Name is already in use](#name-is-already-in-use)
   * [3.8 Save failed](#save-failed)
   * [3.9 Saved games are not listed](#saved-games-are-not-listed)
   * [3.10 Stutters when moving the mouse](#stutters-when-moving-the-mouse)
   * [3.11 Video initialization failure](#video-initialization-failure)
   * [3.12 You cannot run Dungeon Siege II in a resolution higher than your desktop](#you-cannot-run-dungeon-siege-ii-in-a-resolution-higher-than-your-desktop)
* [4.0 Modding](#modding)
   * [4.1 DS2TankViewer doesn't work](#ds2tankviewer-doesnt-work)
   * [4.2 Elys Succubus Manager cannot run DS2/BW](#elys-succubus-manager-cannot-run-ds2bw)
   * [4.3 Elys Succubus Manager doesn't find BW](#elys-succubus-manager-doesnt-find-bw)
   * [4.4 Elys Succubus Manager doesn't load](#elys-succubus-manager-doesnt-load)
   * [4.5 Install the DS2 Tool Kit on the Steam version](#install-the-ds2-tool-kit-on-the-steam-version)
   * [4.6 Make DungeonSiege2Mod work on the Steam version](#make-dungeonsiege2mod-work-on-the-steam-version)
   * [4.7 Tank Creator doesn't work](#tank-creator-doesnt-work)
* [5.0 Links](#links)
* [6.0 Credits](#credits)
* [7.0 Disclaimer](#disclaimer)

# Glossary

Shortcuts used throughout this document:

BW = Broken World  
DS2 = Dungeon Siege 2  
GPU = Graphics Processing Unit (graphics card)  
MP = Multiplayer  
SP = Singleplayer  
\<config-file\> = "\<path-to-docs\>\DungeonSiege2.ini"  
\<config-file-BW\> = "\<path-to-docs-BW\>\DungeonSiege2BrokenWorld.ini"  
\<gpu-model\> = actual name of your GPU (ex: "NVIDIA GeForce GTX 1070")  
\<path-to-docs\> = "%USERPROFILE%\Documents\My Games\Dungeon Siege 2"  
\<path-to-docs-BW\> = "%USERPROFILE%\Documents\My Games\Dungeon Siege 2 Broken World"  
\<path-to-game\> = the game directory (ex: "%PROGRAMFILES(X86)%\Steam\steamapps\common\Dungeon Siege 2")

Please note that while this document is based on the Steam version (combined with [Killah's fix](#enable-bw--extras)), I did my best to accommodate retail users and those not using BW. Some steps may be different and a few issues may not happen on the retail version.

# Guides

## Add the game on GameRanger

1. Download and run [Symlinker](https://amd989.github.io/Symlinker) (click on "Download Standalone Executable"). It's a front-end for the mklink command.
2. In Symlinker, make a directory junction to your game directory in Program Files:

   ![](https://cdn.discordapp.com/attachments/354176540960882689/752654319890989176/unknown.png)

3. In GameRanger, hit "Edit -\> Options -\> Games -\> Dungeon Siege 2 -\> Browse" then select "DungeonSiege2.exe" from Program Files:

   ![](https://cdn.discordapp.com/attachments/354176540960882689/752655137390067872/unknown.png)

## Change the FOV

1. Download this [archive](http://www.wsgf.org/f/u/contrib/dr/255/hacks/DS2%20Files.zip).
2. Place the correct file for your resolution in "\<path-to-game\>\Resources".

## Enable BW + Extras

Follow the instructions from [Killah's guide](https://steamcommunity.com/sharedfiles/filedetails/?id=1165078098).

## Increase shadow resolution
 
Open "\<path-to-game\>\system_detail.gas" and change the 4 occurrences of "shadow_tex_size = xxx" to something like 512/1024.

## Increase UI size

If you play the game at higher resolutions (like 1080p), the UI won't scale and will become tiny. There is a workaround that involves rendering the game at a specific resolution and the UI at a lower resolution (effectively making it bigger):

1. Download the latest version of [dgVoodoo2](http://dege.freeweb.hu/dgVoodoo2/dgVoodoo2).
2. Open the downloaded archive and extract dgVoodoo.conf, dgVoodooCpl.exe and "MS\x86\D3D9.dll" to \<path-to-game\>.
3. Run dgVoodooCpl.exe, go to the DirectX tab and select "GeForce FX 5700 Ultra" from the Videocard drop down list (this will get rid of a warning at launch).
4. From the same tab, select your native resolution from the Resolution drop down list and hit OK.
5. Set the game at the resolution you want the UI to be scaled to (typically 720p or lower).

Note: disable third-party overlays and frame limiters if your game crashes at launch or slows down when moving the mouse.

## Play borderless fullscreen

There are multiple programs that allow games to run borderless fullscreen (you can find an exhaustive list [here](https://www.pcgamingwiki.com/wiki/Glossary:Borderless_fullscreen_windowed)), however for the sake of simplicity, we'll only cover one of them here.

1. Download [Fullscreenizer](https://github.com/KasumiL5x/Fullscreenizer/releases/tag/v1.0) and run it.
2. Run the game in [windowed](#play-windowed) mode.
3. Switch back to Fullscreenizer.
4. If the game doesn't appear in the list, click on "Show All", select "Dungeon Siege II" and click on "Add".
5. Select the game in the list and press the Fullscreenize button (or use your hotkey combination), preferably after loading a game.

Note: the main menu UI has a fixed resolution and will be broken, repeat step 5 again to make the game windowed again.

## Play online

If you want to play online, there are 2 solutions that I can confirm are working: GameRanger and ZeroTier. Other virtual LAN softwares may work, but I haven't tried them (I never got Hamachi to let you see games though).

GameRanger is fairly easy to set up, just check [Add the game on GameRanger](#add-the-game-on-gameranger) and the rest will be pretty self-explanatory (you may need to [port-forward](https://portforward.com/router.htm) UDP 16000). However, since the game is not run from Steam but from GameRanger, your hours won't be tracked. You also won't be able to use Elys DS2 Succubus Manager as GameRanger runs the original executable.

That's where ZeroTier comes into play. It's harder to set up but seems to work better and will allow you to use Elys DS2 Succubus Manager. Please follow the steps below to configure it.

Graphical version:

https://support.parsecgaming.com/hc/en-us/articles/115002766652-Setting-Up-A-VPN-To-Play-Games-On-A-Virtual-Local-Network (ignore the last steps about Parsec)

Text version:

Please note that these steps are for Windows 10. They may be slightly different on Windows 8.1 or lower.

1. Create an account on https://my.zerotier.com and sign in.
2. Download, install and run ZeroTier.
3. Right click ZeroTier in the notification area of your taskbar.  
    3a. (If hosting) Select "Create and Join Network" and hit Yes in the Windows network prompt.  
    3b. (If joining) Select "Join Network...", input the network ID given to you by the user hosting (displayed under "Basics -> Network ID" in Step 7), then skip to Step 13.
4. Right-click ZeroTier in the bottom right again
5. Select "ZeroTier Central".
6. Go to the Networks tab.
7. Click on the network listed.
8. Under "Basics -> Name", give a familiar name to your network.
9. Under "Basics -> Access Control", select Private if you want to manually authorize anyone who attempts to join (you can do this by scrolling down to the Members section and checking the box under "Auth?").
10. Under "Advanced -> IPv4 Auto-Assign", select Easy then one of the IP formats in the list.
11. Under "Advanced -> IPv6 Auto-Assign", make sure all boxes are unchecked.
12. Under "Advanced -> Broadcast", check the box labeled "Enable Broadcast (ff:ff:ff:ff:ff:ff)".
13. In Windows, go to "Control Panel -> Network and Sharing Center".
14. Double-click on the adapter named "ZeroTier One" followed by the network ID (it's a 16-characters alphanumeric string). If it's not in the list, go to "C:\ProgramData\ZeroTier\One\tap-windows\x64", right-click "zttap300.inf" and hit Install.
15. Click on Configure.
16. Go to the Advanced tab, set "Non-Admin Access" to Allowed and click on OK.
17. Make sure "Internet Protocol Version 6 (TCP IPv6)" is unchecked.
18. Double-click on "Internet Protocol Version 4 (TCP IPv4)".
19. Make sure both "Obtain an IP address automatically" and "Obtain DNS server address automatically" are selected.
20. Click on Advanced.
21. Uncheck "Automatic metric" and set it to 1 (this will ensure the game uses the ZeroTier adapter instead of your main network adapter).
22. Hit OK until all windows are closed.
23. Attempt to host/join via Local Network in Dungeon Siege 2.

## Play windowed

Add the "fullscreen=false" launch parameter. See the following instructions for [shortcuts](https://www.pcgamingwiki.com/wiki/Glossary:Command_line_arguments#Desktop_shortcuts), [Steam](https://www.pcgamingwiki.com/wiki/Glossary:Command_line_arguments#Steam) or [GOG Galaxy](https://www.pcgamingwiki.com/wiki/Glossary:Command_line_arguments#GOG_Galaxy_2.0).

Note: the instructions from [Increase UI size](#increase-ui-size) will not work in windowed mode.

# Issues fixed

## Camera spinning too fast

This only happens when using middle-click while running the game in windowed mode through an executable that was hex-edited to show the mouse cursor while playing fullscreen.

- For DS2, use the original/Steam executable.
- For DS2BW ([Killah's fix](#enable-bw--extras)), use this [executable](https://www.mediafire.com/file/9ivessmxpqapi9n/DungeonSiege2BW_windowed.exe).

## Crash/exception

It can be caused by literally anything. Here are a few common fixes I've gathered since I started playing this game:
 
- Run "\<path-to-game\>\DSVideoConfig.exe" and switch your driver to "\<gpu-model\> - Hardware" (or its TnL equivalent).
- Run the game as administrator.
- Run the game in compatibility mode (try all of them).
- Run the game from the executable instead of Steam.
- Run the game on your other GPU (if you have one).
- Run the game [windowed](#play-windowed).
- Your latest saved game is corrupted, replace it with a backup.
- Some mods can conflict with each other. Find and remove conflicting mods.
- Some mods don't work on BW. Find and remove incompatible mods, then look for similar mods compatible with BW.
- Make the game recognize your GPU with this [guide](https://steamcommunity.com/sharedfiles/filedetails/?id=780053070).
- Use [dgVoodoo2](http://dege.freeweb.hu/dgVoodoo2/dgVoodoo2.html).

## Join button doesn't work

In the MP lobby, if nothing happens when clicking the Join button, make sure everyone has the same mods and executable (DS2 doesn't display a warning like in [DS1](https://github.com/GenesisFR/DS1TroubleshootingGuide#incompatible-version)).

## LAN games are not visible

1. Go to "Control Panel -> Programs and Features -> Turn Windows features on or off -> Legacy Components" and enable DirectPlay.
2. Go to "Control Panel -> Network and Sharing Centre -> Advanced sharing settings" and turn on network discovery.

Note: this is for physical LAN games (not VPN).

## Missing/corrupted DLLs

If you see an error about a missing/corrupted DLL, copy the following DLLs from "\<path-to-game\>\system\" to "\<path-to-game\>\":

- binkw32.dll
- mss32.dll

Somehow the game can't find them on some systems. This makes sure it does.

## Mouse cursor is missing

For DS2, see [PCGamingWiki](https://pcgamingwiki.com/wiki/Dungeon_Siege_II#No_mouse_cursor).  
For BW, use [Killah's fix](#enable-bw--extras).

## Name is already in use

This error occurs when hosting a LAN game because the game is using the wrong network adapter. You have to make it use another network adapter (preferably your virtual LAN network adapter) in one of these ways.

Method 1:

1. Go to "Control Panel -> Network and Sharing Centre -> Change adapter settings".
2. Double-click on your virtual LAN network adapter (ex: ZeroTier).
3. Make sure "Internet Protocol Version 6 (TCP IPv6)" is unchecked.
4. Double-click on "Internet Protocol Version 4 (TCP IPv4)" (make sure it's checked).
5. Click on Advanced.
6. Uncheck "Automatic metric" (MTU) and set it to 1.

If it didn't work, revert your changes and try with your main network adapter.

Method 2:

1. Go to "Control Panel -> Network and Sharing Centre -> Change adapter settings".
2. Disable your virtual LAN network adapter OR disable your main network adapter.
3. If you have other network adapters, disable them as well.
4. Go back to your game and click on the "Local Network" button again.
5. Reenable the network adapter you disabled in step 2.

Note: only one network adapter must have its MTU set to 1 at any given time!

## Save failed

When trying to save the game, you may get a message saying "Save failed" and no save is created under \<path-to-docs\>.

- Your antivirus/antimalware/ransomware protection is at fault. Add the game as an exception or disable it.
- You have a username with special (non-latin) characters. Change your username so it only uses latin characters.
- Run the game as admin.

Note: it happens in a few other games too.

Source: https://steamcommunity.com/app/39200/discussions/0/2619339453457265287

## Saved games are not listed

Saved games created while using different mods won't be displayed and therefore cannot be loaded. Run the game through Elys DS2 Succubus Manager to load them.

## Stutters when moving the mouse

This is caused by the NVIDIA drivers for Cyberpunk (460.79). The problem was fixed in 466.11. If it's still not fixed for you for some reason, use older drivers. You can use this [link](https://www.nvidia.com/Download/Find.aspx?lang=en-us) to find them.

## Video initialization failure

The game is using a resolution that is not natively supported by your GPU. The error may also happen when alt-tabbing. Several solutions are available:

- Add a [custom resolution](https://appuals.com/how-to-create-custom-resolutions-on-windows-7-8-or-10).
- Use one of the standard resolutions (ex: 1024x768, 1280x720, 1920x1080).
- Run the game in [windowed](#play-windowed) mode.
- Use dgVoodoo (check [Increase UI size](#increase-ui-size) for installation instructions).

## You cannot run Dungeon Siege II in a resolution higher than your desktop

Lower the game's height (see [Playing Dungeon Siege 2 with a Custom Resolution](https://www.wsgf.org/dr/dungeon-siege-ii)) so that it corresponds to your desktop's height minus at least 40 pixels (it can be more) to account for the borders (ex: 1920x1080 -\> 1920x1040).

# Modding

## DS2TankViewer doesn't work

If the official DS2TankViewer doesn't start, you can try the [unofficial TankViewer2](https://www.siegetheday.org/?q=node/2951) instead.

## Elys Succubus Manager cannot run DS2/BW

If you see an error like "Impossible to start DungeonSiege2.exe (Broken World)!", it may be because you're running the game as admin or in compatibility mode. Run Succubus as admin or in compatibility mode instead (try all of them).

## Elys Succubus Manager doesn't find BW

If you see an error like "Dungeon Siege 2 Broken World installation directory was not found in the Windows registry!", download the [reg patch](https://github.com/GenesisFR/DungeonSiegeRegPatches) and run it from \<path-to-game\> (select option 2).

## Elys Succubus Manager doesn't load

If you don't see the new races (nymph, succubus, vampire, daemon, drow) added by the modlet as well as the Elys loading screen when starting/loading a game, it means it somehow didn't load.

- In Elys, make sure "Load Succubus Modlet" is checked.
- If that didn't solve the problem, uninstall and reinstall Elys.

## Install the DS2 Tool Kit on the Steam version

1. Download the [reg patch](https://github.com/GenesisFR/DungeonSiegeRegPatches) and run it from \<path-to-game\> (select option 1).
2. If you're not using Killah's fix, you must also place this [file](https://www.mediafire.com/file/90262526a2w34xu/SETUPENU.DLL) in \<path-to-game\> before running the installer.

## Make DungeonSiege2Mod work on the Steam version

Download the [reg patch](https://github.com/GenesisFR/DungeonSiegeRegPatches) and run it from \<path-to-game\> to make DungeonSiege2Mod find your game.
 
DungeonSiege2Mod uses SmarteSecure DRM disc check so you'll need to have disc 1 of DS2 in your disc drive or it'll refuse to run.

If you don't want to go this route, I created a [mini image](https://www.mediafire.com/file/zuib6l7xjjx6nvc/DS2_1+mini+image.iso) that will satisfy the disc check.

Just mount the ISO with Windows 10 File Explorer or with a third party software (like WinCDEmu) before running DungeonSiege2Mod.

If you have a "Couldn't register file.tmp" popup followed by a SmarteSecure popup, it means the location you're trying to run it from has permission issues. Run DS2Mod as admin or move it elsewhere.

You may also have a few "ATLCOMHelper Exception" popups. You can safely ignore those and DungeonSiege2Mod will run. To get rid of them, either use the DungeonSiege2Mod shortcut in the toolkit installation directory or place DungeonSiege2Mod in \<path-to-game\> and run it from there.

Note: DungeonSiege2Mod isn't compatible with BW so move all files starting with 'x' in "\<path-to-game\>\Resources" somewhere else.

## Tank Creator doesn't work

If nothing happens when clicking on the Create button in Tank Creator, make sure it's added to the exclusion list of your antivirus.

# Links

- http://ds2.bplaced.net/sysdat/ ("system_detail.gas" configurator)
- https://www.siegetheday.org/?q=node/1290 (Elys DS2 Succubus Manager v10)

# Credits
 
This document wouldn't have been possible without the following people:
 
- [Antrad2020](https://antonior-software.blogspot.com)
- [doa_92](https://steamcommunity.com/id/doa_92)
- Eibhleann#3066 (Discord)
- [loadedpinky137](https://steamcommunity.com/id/Now_Loading247)
- Killah
- RandallTVandal#9569 (Discord)
- shockingboring#0041 (Discord)
- sadowson#5553 (Discord)
- Whibbleton#5836 (Discord)
- Wiesshund#1964 (Discord)
- Zeotile#9063 (Discord)

And the following resources:
 
- https://pcgamingwiki.com/wiki/Dungeon_Siege_II
- http://www.wsgf.org/dr/dungeon-siege-ii
- Steam Community forums/guides
 
Thanks a lot for your help!
 
# Disclaimer
 
I won't be held responsible if you mess up your game or saved game after using one of these fixes. You do it at your own risk!
 
You're not allowed to put this document in raw form anywhere, out of respect (it took me 2 years to compile it). Just share the GitHub link.
