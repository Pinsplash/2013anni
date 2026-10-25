This repo is meant to fix problems that arise when attempting to use the latest versions of HL2 maps in the 2013 SP SDK. The 2013 SDK is essentially a snapshot of Half-Life 2 as it was in 2013. Changes to HL2 since 2013 have largely not been mirrored to the SDK.

This repo does not give feature parity with current HL2. These are just the minimum requirements needed to not have to ask users to switch to the steam_legacy branch for mods using HL2 maps (such as Half-Life 2 Chaos) while also minimizing required storage space by taking assets from the HL2 installation as much as possible. (You already had to do this to some degree, unless you were going to ship Valve's maps.)

We use a code-based hack that was originally used by Half-Life Deathmatch: Source to mount Half-Life: Source's content. (The SP branch doesn't have the `appid_` keyword which the MP branch uses in gameinfo.txt.)

Things to know:
* Some behavior depends on the mod folder name. Look for references to `mod_hl2`, `mod_episodic`, and `mod_ep2` in the `CServerGameDLL::DLLInit` function, the `gTitleComments` array, the localization files in the `resource` folders, `titles.txt` in the `scripts` folders, the `gameinfo.txt` files for the ep1 and 2 mods, and of course the VPC files.
  * The error "Unknown -game parameter" will appear if the mod names are not updated in `CServerGameDLL::DLLInit`.
* The Episode One mod expects the base HL2 mod to be installed, and the Episode Two mod expects the Ep1 and HL2 mods to be installed. (In the same `sourcemods` folder.)
* The hack requires that `serverevents.res`, `chapterbackgrounds.txt`, and the background menu textures are kept in the mod folder. There will be problems if they are removed.
* Use of non-engine tools like Hammer or HLMV is not common for this type of mod, but if it is desired, you must edit gameinfo.txt. See gameinfo.txt for more info.
* The Episodic project is still used for both Episodes. To make it open Episode One, `-game` has to be a path to the `mod_episodic` folder, and vice versa for `mod_ep2`.
* The following additional patches have been applied:
  * Fixed dropship container gun not turning.
  * Fixed screen flashing from all damage after being hit by `DMG_ACID` damage once.
  * Replaced `hl2_episodic` convar with a new one called `mod_running` which tells precisely which mod is being run. See `CServerGameDLL::DLLInit` to understand how it works.
  * Fixed RPG AI trace bug. (Controlled by convar `ai_rpg_clearshotfix`.)
* Planned additions:
  * Allow holding jump button. (Convar)
  * Per-map CFG files like in TF2.
  * Consolidate HL2/Episodic into one project.
