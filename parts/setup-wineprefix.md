Creating a new wineprefix configured best for [compatible apps/games](https://github.com/Mantas-2155X/illusion-wine-guide/blob/master/parts/notes.md).

**Steps:**
* Create, set up the wineprefix by running the following in terminal:
  * `export WINEPREFIX="~/.wine_custom"` (path to your new wineprefix, change as needed)
  * `winetricks corefonts dxvk dotnet472 dotnet35`    (skip `dxvk` if using MacOS)
  * If asked to install mono, gecko, click no
* Allow the native winhttp wrapper be loaded
  * Type `wine reg add "HKEY_CURRENT_USER\Software\Wine\DllOverrides" /v winhttp /t reg_sz /d native,builtin /f`in the terminal
* Disable WPF hardware acceleration to prevent graphical glitches with launchers, dnspy
  * Type `wine reg add "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics" /v DisableHWAcceleration /t REG_DWORD /d 1 /f` in the terminal
