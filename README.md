# DS2TroubleshootingGuide

Shortcuts used throughout this document:
 
BW = Broken World  
DS2 = Dungeon Siege 2  
GPU = Graphics Processing Unit (graphics card)  
MP = Multiplayer  
SP = Singleplayer  
\<config-file\> = "\<path-to-docs\>\DungeonSiege2.ini"  
\<config-file-BW\> = "\<path-to-docs-LOA\>\DungeonSiege2BrokenWorld.ini"  
\<gpu-model\> = actual name of your GPU (ex: "NVIDIA GeForce GTX 1070")  
\<path-to-docs\> = "%USERPROFILE%\Documents\My Games\Dungeon Siege 2"  
\<path-to-docs-BW\> = "%USERPROFILE%\Documents\My Games\Dungeon Siege 2 Broken World"  
\<path-to-game\> = your installation directory (ex: "%PROGRAMFILES(X86)%\Steam\steamapps\common\Dungeon Siege 2")

Please note that while this document is based on the Steam version (combined with Killah's fix), I did my best to accommodate retail users and those not using BW. Some steps may be different and a few issues may not happen on the retail version.

===== Guides =====

== Add the game on GameRanger ==

1. Download and run https://amd989.github.io/Symlinker (it's just a front-end for the mklink command).
2. In Symlinker, make a directory junction to your game directory in Program Files: https://cdn.discordapp.com/attachments/354176540960882689/538078046176149504/unknown.png
3. In GameRanger, hit "Edit -> Options -> Games -> Dungeon Siege 2 -> Browse" then select "DungeonSiege2.exe" from Program Files: https://cdn.discordapp.com/attachments/354176540960882689/538081835608178700/unknown.png

== Change the FOV ==

1. Download this archive: http://www.wsgf.org/f/u/contrib/dr/255/hacks/DS2%20Files.zip
2. Place the correct file for your resolution in "\<path-to-game\>\Resources".

== Enable BW + Extras ==

Follow the instructions from Killah's guide: https://steamcommunity.com/sharedfiles/filedetails/?id=1165078098

== Increase shadow resolution ==
 
Open "\<path-to-game\>\system_detail.gas" and change the 4 occurrences of "shadow_tex_size = xxx" to something like 512/1024.

== Increase UI size ==

If you play the game at higher resolutions (like 1080p), the UI won't scale and will become tiny. There is a workaround that involves rendering the game at a specific resolution and the UI at a lower resolution (effectively making it bigger):

1. Download the latest version of dgVoodoo2: http://dege.freeweb.hu/dgVoodoo2/dgVoodoo2.html
2. Open the downloaded archive and extract dgVoodoo.conf, dgVoodooCpl.exe and "MS\x86\D3D9.dll" to \<path-to-game\>.
3. Run dgVoodooCpl.exe, go to the DirectX tab and select "GeForce FX 5700 Ultra" from the Videocard drop down list (this will get rid of a warning at launch).
4. From the same tab, select your native resolution from the Resolution drop down list and hit OK.
5. Set the game at the resolution you want the UI to be scaled to (typically 720p or lower).

Note: disable third-party overlays (like MSI Afterburner) if your game crashes at launch or slows down when moving the mouse.

== Play online ==

If you want to play online, there are 2 solutions that I can confirm are working: GameRanger and ZeroTier. Other virtual LAN softwares may work, but I haven't tried them (I never got Hamachi to let you see games though).

GameRanger is fairly easy to set up, just check the "Add the game on GameRanger" section and the rest will be pretty self-explanatory (you may need to port-forward UDP 16000). However, since the game is not run from Steam but from GameRanger, your hours won't be tracked. You also won't be able to use Elys DS2 Succubus Manager as GameRanger runs the original executable.

That's where ZeroTier comes into play. It's harder to set up but seems to work better and will allow you to use Elys DS2 Succubus Manager. Please follow the steps below to configure it.

Graphical version:

https://support.parsecgaming.com/hc/en-us/articles/115002766652-Setting-Up-A-VPN-To-Play-Games-On-A-Virtual-Local-Network (ignore the last steps about Parsec)

Text version:

Please note that these steps are for Windows 10. They may be slightly different on Windows 8.1 or lower.

1. Create an account on https://www.zerotier.com and sign in.
2. Download and install ZeroTier.
3. Right click ZeroTier in the notification area of your taskbar.
    3a. (If hosting) Select "Create+Join a network".
    3b. (If joining) Select "Join Network...", input the network ID given to you by the user hosting, then skip to Step 13.
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
14. Double-click on the adapter named "ZeroTier One" followed by the network ID (it's a 16-characters alphanumeric string).
15. Make sure "Internet Protocol Version 6 (TCP IPv6)" is unchecked.
16. Double-click on "Internet Protocol Version 4 (TCP IPv4)".
17. Make sure both "Obtain an IP address automatically" and "Obtain DNS server address automatically" are selected.
18. Click on Advanced.
19. Uncheck "Automatic metric" and set it to 1 (this will ensure the game uses the ZeroTier adapter instead of your main network adapter).
20. Hit OK until all windows are closed.
21. Attempt to host/join via Local Network in Dungeon Siege 2.

Note: if the ZeroTier adapter isn't listed at step 14, go to "C:\ProgramData\ZeroTier\One\tap-windows\x64", right-click "zttap300.inf" and hit Install.

===== Issues fixed =====

== Camera spinning too fast ==

This only happens when using middle-click while running the game in windowed mode through an executable that was hex-edited to show the mouse cursor while playing fullscreen.

For DS2, use the original/Steam executable.
For DS2BW (Killah's fix), use this executable: https://www.mediafire.com/file/9ivessmxpqapi9n/DungeonSiege2BW_windowed.exe

== Crash/exception ==

It can be caused by literally anything. Here are a few common fixes I've gathered since I started playing this game:
 
- Run "\<path-to-game\>\DSVideoConfig.exe" and switch your driver to "\<gpu-model\> - Hardware" (or its TnL equivalent).
- Run the game as administrator.
- Run the game in compatibility mode (try all of them).
- Run the game from the executable instead of Steam.
- Run the game on your other GPU (if you have one).
- Your latest saved game is corrupted, replace it with a backup.
- Some mods can conflict with each other. Find and remove conflicting mods.
- Some mods don't work on BW. Find and remove incompatible mods, then look for similar mods compatible with BW.

== LAN games are not visible ==

1. Go to Control Panel -> Programs and Features -> Turn Windows features on or off -> Legacy Components -> Enable DirectPlay.
2. Go to Control Panel -> Network and Sharing Centre -> Advanced sharing settings -> Turn on network discovery.

Note: this is for physical LAN games (not VPN).

== Mouse cursor is missing ==

See https://pcgamingwiki.com/wiki/Dungeon_Siege_II#No_mouse_cursor.

== Name is already in use ==

This error occurs when hosting a LAN game because the game is using the wrong network adapter. You have to make it use another network adapter (preferably your virtual LAN network adapter) in one of these ways.

Method 1:

1. Go to Control Panel -> Network and Sharing Centre -> Change adapter settings.
2. Double-click on your virtual LAN network adapter (ex: ZeroTier).
3. Make sure "Internet Protocol Version 6 (TCP IPv6)" is unchecked.
4. Double-click on "Internet Protocol Version 4 (TCP IPv4)" (make sure it's checked).
5. Click on Advanced.
6. Uncheck "Automatic metric" and set it to 1.

If it didn't work, revert your changes and try with your main network adapter.

Method 2:

1. Go to Control Panel -> Network and Sharing Centre -> Change adapter settings.
2. Disable your virtual LAN network adapter OR disable your main network adapter.
3. Go back to your game and click on the "Local Network" button again.
4. Reenable the network adapter you disabled in step 2.

Note: only one network adapter must have its MTU set to 1 at any given time!

== Save failed ==

When trying to save the game, you may get a message saying "Save failed" and no save is created under \<path-to-docs\>.

- Your antivirus/antimalware/ransomware protection is at fault. Add the game as an exception or disable it.
- You have a username with special (non-latin) characters. Change your username so it only uses latin characters.
- Run the game as admin.

Note: it happens in a few other games too.

Source: https://steamcommunity.com/app/39200/discussions/0/2619339453457265287

== Saved games are not listed ==

Saved games created while using different mods won't be displayed and therefore cannot be loaded. Run the game through Elys DS2 Succubus Manager to load them.

===== Modding =====

== DS2TankViewer doesn't work ==

If the official DS2TankViewer doesn't start, you can try the unofficial TankViewer2 instead: https://www.siegetheday.org/?q=node/2951

== Elys DS2 Succubus Manager cannot run DS2/BW ==

If you see an error like "Impossible to start DungeonSiege2.exe (Broken World)!", run Succubus as admin or in compatibility mode (try all of them).

== Elys DS2 Succubus Manager doesn't find BW ==

If you see an error like "Dungeon Siege 2 Broken World installation directory was not found in the Windows registry!", download the Reg patcher from Killah's fix (see above) and run it from \<path-to-game\> (select option 2).

== Install the Dungeon Siege 2 Tool Kit on the Steam version ==

1. Download the Reg patcher from Killah's fix (see above) and run it from \<path-to-game\> (select option 1).
2. If you're not using Killah's fix, place this file in \<path-to-game\> before running the installer: https://www.mediafire.com/file/90262526a2w34xu/SETUPENU.DLL

== Make DungeonSiege2Mod work on the Steam version ==

Download the Reg patcher from Killah's fix (see above) and run it from \<path-to-game\> to make DungeonSiege2Mod find your game.
 
DungeonSiege2Mod uses SmarteSecure DRM disc check so you'll need to have disc 1 of DS2 in your disc drive or it'll refuse to run.

If you don't want to go this route, I created a mini image that will satisfy the disc check: https://www.mediafire.com/file/zuib6l7xjjx6nvc/DS2_1+mini+image.iso

Just mount the ISO with Windows 10 File Explorer or with a third party software (like WinCDEmu) before running DungeonSiege2Mod.

If you have a "Couldn't register file.tmp" popup followed by a SmarteSecure popup, it means the location you're trying to run it from has permission issues. Run DS2Mod as admin or move it elsewhere.

You may also have a few "ATLCOMHelper Exception" popups. You can safely ignore those and DungeonSiege2Mod will run. To get rid of them, either use the DungeonSiege2Mod shortcut in the toolkit installation directory or place DungeonSiege2Mod in \<path-to-game\> and run it from there.

Note: DungeonSiege2Mod isn't compatible with BW so move all files starting with 'x' in "\<path-to-game\>\Resources" somewhere else.

===== Links =====

- http://ds2.bplaced.net/sysdat/ ("system_detail.gas" configurator)
- https://www.siegetheday.org/?q=node/1290 (Elys DS2 Succubus Manager v10)

===== Credits =====
 
This document wouldn't have been possible without the following people:
 
- Antrad2020 (https://antonior-software.blogspot.com)
- doa_92 (https://steamcommunity.com/id/doa_92)
- Eibhleann#3066 (Discord)
- Killah (https://steamcommunity.com/profiles/76561198156984417)
- sadowson#5553 (Discord)
- Whibbleton#5836 (Discord)
- Wiesshund#1964 (Discord)
- Zeotile#9063 (Discord)

And the following resources:
 
- https://pcgamingwiki.com/wiki/Dungeon_Siege_II
- http://www.wsgf.org/dr/dungeon-siege-ii
- Steam Community forums/guides
 
Thanks a lot for your help!
 
===== Disclaimer =====
 
I won't be held responsible if you mess up your game or saved game after using one of these fixes. You do it at your own risk!
 
You're not allowed to put this document in raw form anywhere, out of respect (it took me a year to compile it). Just share the GitHub link.
