Creating a new wineprefix configured best for [compatible apps/games](https://github.com/Mantas-2155X/illusion-wine-guide/blob/master/parts/notes.md).

**Steps:**
* Create, set up the wineprefix by running the following in terminal:
  * `export WINEPREFIX="/home/username/.wine_custom"` (path to your new wineprefix, change as needed)
  * `winetricks corefonts dxvk dotnet472 dotnet35`    (skip `dxvk` if using MacOS)
  * If asked to install mono, gecko, click no
* Configure the wineprefix by running `winecfg` in the same terminal
  * In the 'Applications' tab change the windows version to 'Windows 7'
  * In the 'Libraries' tab type 'winhttp' (without quotes) and click 'Add'
  * Set the new added values to 'native,builtin' by clicking 'Edit'
  * Apply & OK
* Disable WPF hardware acceleration to prevent graphical glitches with launchers, dnspy
  * Type `wine regedit` in the same terminal
  * Navigate to `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\` (create if doesn't exist)
  * Right click the Key and create a new DWORD `DisableHWAcceleration`
  * Double click the new added value and set it to 1
  * Close `regedit`
