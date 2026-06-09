The 2013 SDK is essentially a snapshot of Half-Life 2 as it was in 2013. Changes to HL2 since 2013 have largely not been mirrored to the SDK. This repo is meant to fix problems that arise when attempting to use the latest versions of HL2 maps in the 2013 SDK.

This repo does not give feature parity with current HL2. These are just the minimum requirements needed to not have to ask users to switch to the steam_legacy branch for mods using HL2 maps (such as Half-Life 2 Chaos).

The gameinfo.txt changes use relative paths to find the current HL2 folder to get its maps. (The Singleplayer SDK doesn't have a way to find the folders by appid.) Users have to either install Source SDK Base 2013 Singleplayer in the same Steam directory as Half-Life 2, or put the mod in the `sourcemods` folder of the same Steam directory as Half-Life 2.

Things to know:
* Some behavior depends on the mod folder name. Look for references to `mod_hl2`, `mod_episodic`, and `mod_ep2` in the functions `Flashlight_UseLegacyVersion`, `UpdateChapterRestrictions`, `UpdateRichPresence`, `CNPC_Vortigaunt::Precache`, the `gTitleComments` array, the localization files in the `resource` folders, titles.txt in the `scripts` folders, gameinfo.txt, and of course the VPC files.
* The gameinfo.txt setup has one side effect in making a `common` folder in the repo's root folder containing nothing but a harmless `sound.cache`. This probably means it overwrites the current HL2 `sound.cache` when run from the `sourcemods` folder, but this is still harmless.
* The Episode One mod expects the base HL2 mod to be installed, and the Episode Two mod expects the Ep1 and HL2 mods to be installed. (In the same `sourcemods` folder.)
* The Episodic project is still used for both Episodes. To make it open Episode One, `-game` has to be a path to the `mod_episodic` folder, and vice versa for `mod_ep2`.
* The following additional patches have been applied:
  * Fixed dropship container gun not turning.
  * Fixed screen flashing from all damage after being hit by `DMG_ACID` damage once.
