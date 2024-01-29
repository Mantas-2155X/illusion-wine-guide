**Compatible OS:**
* Linux (all features),
* MacOS (if DXVK is not available, low performance)

**Confirmed working games:**
* AI Syoujo,
* Emotion Creators,
* Harem Mate,
* Honey Select 1,
* Honey Select 2,
* Koikatsu, 
* Koikatsu Sunshine,
* PlayClub,
* PlayHome

**Confirmed working applications:**
* [dnSpy](https://github.com/dnSpy/dnSpy),
* [IllusionLaunchers](https://github.com/IllusionMods/IllusionLaunchers),
* [SB3Utility](https://github.com/enimaroah/SB3Utility)

**Buggy Wine versions to avoid:**
* Wine 5.7,
* Wine 5.8,
* Wine 5.9,
* Wine 5.19,
* Wine 5.22 (very bad)

**Issues:**
* Can't move camera in the game/studio!
  * Seems to be an issue with some Wine versions, downgrade/upgrade your Wine or use [wine-tkg](https://github.com/Mantas-2155X/illusion-wine-guide/blob/master/parts/packages.md).
* dnSpy crashes / IllusionLauncher is fully black!
  * [Disable WPF hardware acceleration](https://github.com/Mantas-2155X/illusion-wine-guide/blob/master/parts/setup-wineprefix.md) found in step 3.
* Game crashes / freezes after returning from file dialogs
  * [Disabling fullscreen](https://github.com/Mantas-2155X/illusion-wine-guide/issues/13) might resolve it 
