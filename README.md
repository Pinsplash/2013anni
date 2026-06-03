The 2013 SDK is essentially a snapshot of Half-Life 2 as it was in 2013. Changes to HL2 since 2013 have largely not been mirrored to the SDK. This repo is meant to fix problems that arise when attempting to use the latest versions of HL2 maps in the 2013 SDK.

This repo does not give feature parity with current HL2. These are just the minimum requirements needed to not have to ask users to switch to the steam_legacy branch for mods using HL2 maps (such as Half-Life 2 Chaos).

The gameinfo.txt changes use relative paths to find the current HL2 folder to get its maps. (The Singleplayer SDK doesn't have a way to find the folders by appid.) Users have to either install Source SDK Base 2013 Singleplayer in the same Steam directory as Half-Life 2, or put the mod in the `sourcemods` folder of the same Steam directory as Half-Life 2.

Things to know:
* Some behavior depends on the mod folder name. Look in the functions `Flashlight_UseLegacyVersion`, `UpdateChapterRestrictions`, `UpdateRichPresence`, `CNPC_Vortigaunt::Precache`, the `gTitleComments` array, the localization files in the `resource` folders, and `titles.txt` in the `scripts` folders.
