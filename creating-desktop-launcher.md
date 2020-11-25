Desktop based launcher, slower to make than shell launcher but has features like a custom icon, showing up in application launcher.

**Steps:**
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
