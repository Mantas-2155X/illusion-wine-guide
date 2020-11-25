# illusion-wine-guide

**Notes:**
* Works with KK, AI, EC, PH, HS, HS2, their launchers found in BetterRepack, dnSpy, SB3UtilityGUI
* Please refrain from using Wine versions 5.7 to 5.9, 5.18 as they have issues
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
  * Navigate to `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\` (create if doesn't exist)
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
**Creating a desktop file:**

- Open terminal
- Launch Game from the terminal  
  `WINEPREFIX=/home/username/.wine_kk wine /home/username/Games/Koikatu/InitSetting.exe`
- Create a new text file and paste the following template text into it
  
  ```
  [Desktop Entry]
  Name= Game name here
  StartupWMClass= xprop wm class here
  Exec=env WINEPREFIX=/home/username/.wine_kk wine '/home/username/Games/Koikatu/InitSetting.exe'
  Icon=/home/username/.icons/gameicon.png
  Type=Application
  Categories=Game
  
  ```
  - Change the name to what you want it to be
  - Open a second terminal
  - Get Process name using xprop
    - In the second terminal run `xprop`
    - Click on the game window
    - Find the `WM_CLASS(STRING)` in the xprop output
      
      ```  
      WM_CLASS(STRING) = "honeyselect2.exe", "honeyselect2.exe"
      ```
    - Change the StartupWMClass in the open text file to the one from xprop e.g.
      
      ```
      StartupWMClass=honeyselect2.exe
      ```
  - Get the Icon
    - Open the game executable in an archiver of your choice
    - Extract any of the icons in /.rsrc/ICON/ the higher the number the better the quality
    - Convert the icon from ico to png with the software of your choice
    - Create a .icons folder in your home directory
    - Copy the converted icon to the .icons directory and name it whatever you want
    - Change the icon path to point to that icon
      
      ```
      Icon=/home/username/.icons/gameicon.png
      ```
      
      
  - Save the text file as gamename.desktop
  - Move gamename.desktop to /home/username/.local/share/applications/
  - The game should now show up in your de application launcher like a normal executable 
