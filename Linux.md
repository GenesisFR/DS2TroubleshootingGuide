# DS2TroubleshootingGuide for Linux!
## Dungeon Siege 2 "Vanilla"
Dungeon Siege 2 works well with Steam Proton, but there are a couple of steps that are needed.

 - Enable Steam Play for all other titles under Steam Settings > Steam Play
 - Install DS2
 - Set launch options `PROTON_NO_ESYNC=1 PROTON_USE_WINED3D=1 %command% width=1920 height=1080 fullscreen=false vsync=off maxfps=120 nointro=true`
 - You can now play
 
 ## Enabling *Broken World* extension
 
 See [Killah's Guide](https://steamcommunity.com/sharedfiles/filedetails/?id=1165078098) and follow instructionss to enable Broken World.
 To enable it, there is a registry fix to apply. Sadly, the `.bat` file provided by Killah doesn't work on Linux, so you have to manually add the keys to the game's proton bottle registry.
Write a `.reg` file containing:

```reg
REGEDIT4

[HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\Microsoft Games\DungeonSiege2]
"AppPath"="H:\\.steam\\steam\\steamapps\\common\\Dungeon Siege 2"
"CDPath"="E:\\\\"
"DistroID"=dword:0x0000047c
"DoubleHash"=hex:70,4f,25,e4,d2,b1,f8,ea
"InstallationDirectory"="H:\\.steam\\steam\\steamapps\\common\\Dungeon Siege 2"
"InstalledGroup"="1"
"LangID"=dword:00000009
"Launched"="1"
"PID"="77033-133-5335624-40332"
"Version"="2"
"VersionType"="RetailVersion"

```

Be careful, as the paths may differ on your machine. Those paths are from the point of view of `Proton`. Backslashes need to be escaped. 

You can then use `regedit` with your game's proton prefix and import the `.reg` file.

You should now be able to launch the game. 

## Troubleshooting:

| Error | Cause|
|-------|------|
|"In order to play DS2:BW you must first install the full version of DS2"| The registry fix was not applied correctly. |
|"Block name collision. Parent block has a dir and a second dir child block named 'maps' | Chek your DS2 folder. You may have a `maps` and a `Maps` folder. Copy the content of `maps` into `Maps`, then delete `maps`.|



A big thanks to the community!
