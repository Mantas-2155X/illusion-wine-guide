Shell based launcher, faster to make than desktop launcher but no fancy features like a custom icon.

**Steps:**
* Create a new file for your launcher, eg: `StudioNEOV2.sh`
* Make it executable via file manager or terminal: `chmod +x StudioNEOV2.sh`
* Paste the following content into the launcher:
```
#!/bin/bash

export WINEPREFIX="/home/username/.wine_custom"     # Point to your newly created wineprefix
#export WINEESYNC=1                                 # Slighty better performance, may cause issues. Uncomment to enable
#export WINEFSYNC=1                                 # Slighty better performance, needs fsync compatible kernel, may cause issues. Uncomment to enable

cd "/home/username/Games/HS2/"                      # cd to your game directory

wine ./"StudioNEOV2.exe"                            # Run the executable
```

If using wine-tkg, the last line needs to be changed:
* `/path/to/wine-tkg/bin/wine ./"StudioNEOV2.exe"`

If creating launcher for `SB3Utility`, add the following to the start of the last line:
* `WINEDLLOVERRIDES="d3d11,dxgi=b"`
