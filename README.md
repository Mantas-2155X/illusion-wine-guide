# illusion-wine-guide

**Notes:**
* Works with KK, AI, EC, PH, HS, HS2, their launchers found in BetterRepack, dnSpy, SB3UtilityGUI
* Please refrain from using Wine versions 5.7 to 5.9 as they have issues
* Does not work on Mac. Just buy a PC and don't pay such companies which don't deserve your money
* If BepInEx ships with `version.dll` and your game does not run, rename it to `winhttp.dll`. If it still does not work, get the latest BepInEx from https://github.com/BepInEx/BepInEx/releases

**Required packages:**
* `winetricks`      -- Helper to modify wineprefixes
* `winehq-staging`  -- Staging for better performance

**Download links:**
* https://github.com/Winetricks/winetricks  -- Winetricks
* https://wiki.winehq.org/Download          -- Wine

**Setting up your Wineprefix:**
* Open terminal  
* Create a new wineprefix and set up winetricks  
  * Replace the path with anything you want to use  
  * If asked to install mono, gecko click Cancel  
  * Run the following in terminal  
  `export WINEPREFIX="/home/username/.wine_kk"`  
  `winetricks corefonts dxvk dotnet472 dotnet35`  
* Configure the wineprefix by running `winecfg` in the same terminal
  * In the 'Applications' tab change the windows version to 'Windows 7'
  * In the 'Libraries' tab type 'winhttp' (without quotes) and click 'Add'
  * In the 'Libraries' tab type 'version' (without quotes) and click 'Add'
  * Set the new added values to 'native,builtin' by clicking 'Edit'
  * Apply & OK
* Disable WPF hardware acceleration to prevent graphical glitches with launchers, dnspy
  * Type `wine regedit` in the same terminal
  * Navigate to `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\`
  * Right click the Key and create a new DWORD `DisableHWAcceleration`
  * Double click the new added value and set it to 1
  * Close `regedit`

**Creating a launcher for our new wineprefix:**
 * Create a new `name.sh` file and paste the following
```
#!/bin/bash

export WINEPREFIX="/home/username/.wine_kk"     # Point to your newly created wineprefix
#export WINEESYNC=1                             # Slighty better performance, may cause issues. Uncomment to enable

cd "/home/username/Games/Koikatu/"              # cd to your game directory

wine ./"InitSetting.exe"                        # Run the executable
```
* Set it to executable
* If making shell launcher for SB3UtilityGUI change the last line to the following
```
WINEDLLOVERRIDES="d3d11,dxgi=b" wine ./"SB3UtilityGUI.exe"
```
