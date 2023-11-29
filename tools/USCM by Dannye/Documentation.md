Ultimate Stunter's SCM (USCM) - Documentation - v4c
===================================================

[1\. Introduction](# "Show/Hide associated details")
----------------------------------------------------

**Title:** Ultimate Stunter's SCM

**Author:** Dannye

**Summary:** A "main.scm" mod with the goal of making stunting more user-friendly, by providing features that may be used to streamline some of the tedious processes surrounding finding/preparing stunt attempts, without affecting the stunts themselves.

**Version:** v4c (April 2023)

**Game:** GTA San Andreas (PC), plus the following San Andreas map-mods: "Alien City", and "GTA United"

[2\. Installation](# "Show/Hide associated details")
----------------------------------------------------

Decide which map/mod you want to install this for and which variant of the USCM you wish to use, then enter into the corresponding sub-folder and copy over each of the files into your corresponding game directory:

`main.scm`

Place a copy of this file in your `"\<game-install-location>\data\script"` directory

`script.img`

Place a copy of this file in your `"\<game-install-location>\data\script"` directory

`american.gxt`

Place a copy of this file in your `"\<game-install-location>\text"` directory _(this file is the same regardless of which variant/map-mod you choose)_

Consider making a backup of any existing versions of files before replacing them.

### Regarding Save Games:

*   The `main.scm` files included in this project will be incompatible with savegames created using any other `main.scm` file (including those from a prior version of this project). If you need to keep using a previous savegame it may be preferable to not update to this latest version of the USCM. If you do intend to use this latest USCM, you will need to start with a "New Game" on first use.
*   The San Andreas USCM in this package retains all of the standard mission scripts for the game, so you can stunt as well as play through the game normally, if desired. To prevent this from being an issue for stunters, this USCM also includes code to try and ensure that the entire map is "unlocked" from the beginning (various dynamic game-world objects are set to their end-game state: for example, bridges are open and thus all islands accessible, ramps and parked-vehicle spawns that may only become available after certain missions will be available immediately, etc).

[3\. Controlling the USCM - Overview](# "Show/Hide associated details")
-----------------------------------------------------------------------

USCM features are assigned to specific combinations of in-game actions, which your in-game control settings map to specific buttons on your input device. For example, if a USCM feature uses "Sprint", the button you must press is the one you have mapped to "Sprint" in your game settings (perhaps "Shift", if you use keyboard).

To attempt to create a usable USCM supporting stunters with different input devices and/or control mappings, multiple _variants_ have been included, each differing on the assigned actions for certain features. For whichever variant you pick, you may also wish to make changes to your in-game control mapping to try and make the USCM work best for you.


**Map Support:**

*   This is the first release of the SA USCM which also bundles together equivalent USCMs for some of San Andreas' map-mods: 'Alien City' and 'GTA United'.

**Bug Fixes:**

*   In-Car and Foot-to-Car Teleport Loads have reduced (hopefully eliminated) any chance at unintentionally maintaining some momentum from before the teleport (previously this would lead to the location you were placed at not being the exact position/angle you had saved). In addition, no longer will a teleport load triggered on a bike, immediately before a collision, cause the collision to still register and thus potentially only teleport you on-foot and not with the bike.
*   "Water Respawn" now has a fallback implementation for when it is used in map-mods without defined ped/vehicle paths. When no paths are present (and thus this feature is otherwise unable to detect the nearest reasonable spot of land to place you on), it instead will remove you from the vehicle and automatically activate Jetpack, so you can then fly out of the water. _(This feature is less significant here compared to VC, as in the SA engine you can always manually exit your vehicle while it is underwater - VC requires specific USCM coding to support this)_.
*   A tank (Rhino) set as being "vulnerable" has always ensured that it remained "invulnerable" to explosions, as tanks are always meant to be. However tanks are also supposed to always be "invulnerable" to bullets, so now (unlike previous releases) this "invulnerability" will also always be ensured. (The impact of this bug in prior releases should've been relatively minimised by the fact that the tank has such strong health)
*   X & Y coordinate values of the Stats Overlay will now correctly display the negative symbol for values between 0 and -1.

**Misc:**

*   The "Limited" variant of the USCM has has been given some much-needed attention, significantly increasing the set of USCM features that it supports (still not all of them). Most of the changes relate to new features being supported, rather than changing any existing features/controls/behaviour - the exceptions being the following:
    *   Jetpack Forward movement is now performed by the standard method of on-foot forward movement, like all other variants. No longer does this require its own special button combination. Hopefully the more natural approach will make it easy to get used to this change.
    *   The few 'Default Feature States' where Limited had a different default to everyone else have all been changed to be consistent across all variants now. Note that for those which have been affected, their corresponding feature for toggling their state is included in the newly supported features for this variant, and thus their state can now be changed at-will during gameplay.For a focused run-down of the changes specifically made to this variant, please see the included separate documentation file: "Limited Variant Cheat Sheet".

### Version 4 : April 2021

#### Brand New features / SA-specific changes

**New Features:**

*   Bike Telport Snap-to-North - teleport positions with an angle close to north can be loaded to at perfect-north instead, while on a bike
*   Show last/2ndlast Vehicle - while on foot, have the camera leave and go aim-at/follow one of your prior vehicles
*   Always cut replay on teleport load - have any type of teleport load trigger a clearing of the replay buffer
*   Show Stats Overlay - include coordinate, angle, car speed, car health values on your HUD

**NOS and Hydraulics:**

*   "Add NOS + Hyrdaulics"
    *   Now split into two independant features. The NOS one uses the existing button comination, Hydraulics uses a new one.  
        _Previously: Both were combined into one feature, thus you couldn't add one to your vehicle without the other as well_
    *   These features are now toggles, and thus the coresponding component can be added and removed from the current vehicle.  
        _Previously: The feature only ever attempted to 'add' them to the vehicle, never 'remove' them_
    *   They will now also fully abide by each vehicle's proper support for such components, never adding them unless it is naturally supported in-game.  
        _Previously: Only very basic checks were performed for 'support' before installing them, as such for many vehicles it did try to install them even when the vehicles weren't supposed to support them, which is against the spirit of the USCM (sometimes it was okay, as the game ignored the request, but other times it would indeed install them, then either letting them be used when they shouldn't, or having the vehicle go buggy/weird)_
*   "Trigger NOS" feature will now always work on a vehicle with NOS installed, regardless of how it was done (whether it came that way, it was done via a garage/modshop, or was added by the coresponding USCM feature).  
    _Previously: Only worked for taxis and vehicles where it was added by the USCM itself, and even then sometimes it wouldn't work as expected (when doing stuff involving multiple vehicles, the USCM could 'forget' that it had installed NOS on a vehicle and thus couldn't trigger it here)_

**USCM Variants:**

*   Now have TWO variations of the Streamlined Default (aka 'Dannye' from previous releases) variant. The existing SA one was a mis-mash between following the same approach to the 'ideal keys' to the VC one and also doing its own thing with different 'ideal keys', and thus wasn't as streamlined or consistent as it perhaps could be. To try and produce a more consistent (internally, and with the VC USCM) and streamlined variant, but without affect anyone who has used (and is thus familiar with) the 'Dannye' variant from previous SA USCM releases, I have split the Streamlined Default variant into 2 - one more like what the coresponding varaint of the SA USCM has always been, and one more like the corresponding variant of the VC USCM.

**Water Respawn:**

*   In previous releases, the in-car Water Respawn feature could sometimes spawn your-vehicle upside-down and wedged into the ground. This bug has been fixed. (Note it was only ever an issue in the SA-engine USCM)

#### Updates to features ported from VC-engined USCM (v7)

**Vehicle Spawners:**

*   The 6 additional sets of vehicle spawners have been modified to include vehicles appropriate for SA stunting, as best as I could determine.
*   Slight changes were made to the existing 2nd vehicle spawner for SA:
    *   The Maverick was moved out and to the aircraft-specific set instead
    *   The Caddie and DFT have been added
    *   Extra bikes have been added, and all bikes are now in the front row of the vehicles
    *   Other minor rearranging

**Button Changes:**

*   "Toggle last/2ndlast prior vehicle preference" has extra button in its combo:
    *   Was: AIM + ACTION
    *   Now: AIM + ACTION + LEFTThis was done so now there can be a group of 4 features that all use AIM + ACTION + <direction>, which should make them easier to become familiar with.
*   "Spawn Random Vehicle" has a button combo change for the Streamlined Alternate variant (which didn't previously exist for SA):
    *   Was: SPRINT + FIRE + NEXTWEAP
    *   Now: SPRINT + CROUCHThis was done to assist in being able to have the button combination for the new "Show last/2ndlast Vehicle" features have more similarity with the "Take player to prior vehicle" and "Bring prior vehicle to player" features, which is something I was able to do already for the other variants.

#### Ported from VC-engine USCM (v7)

**Button Changes:**

*   Streamlined Default (aka 'Dannye' from previous releases) variants have swapped the button combos for the "Change Car Colours" and "Toggle Vehicle Vulnerability" features (so now, if you follow the 'ideal button pairings' for these variants, the "Toggle Vehicle Vulnerability" and "Toggle Player Vulnerability" features should be assigned to the same buttons. (It was never intentional to be how it used to be)

**Source Code:**

*   SIGNIFICANT overhaul with improved and simplified code, less repetition, consolidated areas of code dealing with triggering features from key detection, nicer variable/label names, removed unnecessary variables/opcodes/logic, using 'gosubs' to make some code more modular, and improved comments (and many more under-the-hood changes/improvements that wont be described below as they do not noticably affect the user experience)
*   Updated to Sanny Builder syntax (written using build 3.5.1), taking advantage of support for using TRUE/FALSE keywords to represent integers 1/0, the ability for simpler 'if' statements ("if", "if and", "if or"), but still generally sticking to the classic opcode-focused syntax (not adopting any of its higher-level language constructs).
*   An added benefit of these improvements will hopefully be that it will be much easier to customise the USCM now for anyone interested in doing so. Disabling a feature altogether, or changing the controls that trigger it, will be a simpler process (and could all be achieved through minor edits in an early area in the code). For example, if you have previously used the 'Limited - aka (Old) Gamepad' variant of the USCM, and would prefer to stick with it, but wish it had more of the features available in it, activating any of the disabled-by-default features in that USCM it should be as simple as uncommenting the trigger detection code (and deciding what ingame actions you would like to map to that trigger).

**Saving/Loading:**

*   Added new feature to save the game at any time (while on foot, and NOT on a mission). (As a result of this, you can now even save while jetpacking, and when you load the game back later you will still be jetpacking) (You should now also be able to save your game \[and thus things like your teleport locations\] when using a map-mod that doesn't have any other method of saving your game)
*   Ghostown status will now be properly remembered on save/load (previously the game would load as ghosttown disabled, regardless of status when saved, potentially confusing the USCM code such that the next toggle would effectively do nothing)
*   Wanted Level feature will no longer be confused by a save/load (the latter automatically clearing the wanted level, yet previously the USCM code was confused by this, affecting the behaviour of the next attempt to raise/lower the wanted level)

**Interacting with a previous vehicle while on-foot (re: 'Teleport into Vehicle', 'Bring Car to Me', and 'Take Me to Car' features)**

*   New feature to toggle WHICH previous vehicle these features should interract with, the player's previous vehicle or the one prior to that.
*   Removed a bug in the code which determines whether the vehicle is acceptable - it used to accept a vehicle that was both destroyed AND underwater, which it should never have done.

**Vehicle Spawners:**

*   Hopefully fixed/reduced the cases where not every vehicle in a set would spawn (seemed to relate to what direction the player was facing when triggering the spawner, especially east/west)
*   In addition to the existing 2 vehicle spawners, there are now 2 more.
    *   (The 1st and 2nd vehicle sets are unchanged from previous USCM releases)
    *   The 3rd vehicle set ('up') includes other fast cars that weren't covered by the original two spawners.
    *   The 4th vehicle set ('down') includes offroad vehicles, gang-variant vehicles, and vehicles with a back tray.
*   4 becomes 8: if activate a vehicle spawner while jetpacking, it will spawn a different set of vehicles...
    *   The jetpack variant of the 1st set includes water vehicles (boats).
    *   The jetpack variant of the 2nd set includes air vehicles (planes/helicopters).
    *   The jetpack variant of the 3rd set includes service vehicles (police/ambulance/fire/etc).
    *   The jetpack variant of the 4th set includes misc vehicles.
*   Added a new feature 'Random Vehicle Spawner': activating this feature will spawn one random vehicle directly in front of the player.

**Jetpack:**

*   Can now activate ALL on-foot features while jetpacking.
*   Performing a foot-to-car Teleport Load while jetpacking (which couldn't be done previously) will automatically deactivate the jetpack.
*   To further reduce the unintended possibility of a player being able to have jetpack enabled while in a vehicle, I have added an extra trigger for disabling it - in addition to the usual control to turn on/off, also now the 'Enter Vehicle' button will deactivate an enabled jetpack.
*   Added new jetpack controls to support extra movements: strafe-left, strafe-right, move-back.
*   Added the ability to hold 'Sprint' while performing any jetpack movements to 'slow it down' (reduce the distance moved).
*   Can now move in multiple directions (along more than one axis) at a time (eg. forward-and-up, diagonally, etc) (The player will also 'go faster' while doing this)

**Water Respawn:**

*   Can now activate the jetpack while the player is in/under-water on-foot, and as such I have removed the on-foot 'Water Respawn' feature (jetpacking out is much more convenient, and gives better control over where you go)
*   In fact ALL features (appropriate with the current status of the player as on-foot/in-vehicle) can now be performed while the player is in water
*   In-vehicle 'Water Respawn' feature still present, but I have changed the control for it (now that all other features are available while in water, you could accidentally trigger 'Water Respawn' when trying to activate a different feature. The control for in-vehicle 'Water Respawn' is now 'Change Camera' - not ideal perhaps (you may want to press it a few more times afterwards to revert to your preferred camera angle), but it wont clash with any other features - and its likely the feature wont be used too often as you can always use the Teleporting features to get out of the water as well (if have a location saved).
*   If you do perform a 'Water Respawn', the game's attempt at auto-selecting an on-ground coordinate to put you will hopefully now be more appropriate (based on vehicle paths, not character paths, since now the feature is only performed while in a vehicle)

**Weather + Time:**

*   Toggling the weather change feature will now lock the weather at the next weather type in the (no longer random) sequence of in-game weather types.
*   It is now possible to disable locked weather, and return to letting the game control it naturally. This will occur on the next toggle of the weather feature after the last locked-weather option, before restarting back at the first one. However, the "natural game-controller weather" state is only available when time is UNFROZEN (to avoid strange game behaviour), and as such:
    *   if enable frozen time while weather is not locked, we will automatically move on to having locked weather at the first in the sequence
    *   if cycling through the weather types while time is frozen, we will skip over the game-controlled weather option, going straight from last-in-cyle to first-in-cycle.

**Wanted Levels:**

*   To allow for significantly simpler code, I have removed the second of the two '0 stars' states in the Wanted Level feature. "Zero stars (Ignored)" is still there as normal, as the lowest state you can be in, but previously there was an extra state between that and 1 Star called 'Zero starts (Not Ignored)'. This has been removed. At any level after 0 you are treated as "not ignored" anyway, and there is always the possibility to raise/lower the level as needed, so hopefully it is no loss. (The only thing no longer possible now is to have the player able to be 'carjacked', which was only previously supported in that state I have removed, but hopefully stunters had no desire for that anyway).
*   No more text message display to say which wanted level you have set it to, when using this function, now the messages shown will only distinguish between 0 stars and some stars. (This was also done to simplify the code - but again, if you want a specific level hopefully you will be showing the HUD to get a more accurate indication of your stars anyway, and thus no need for a message as well)

**Input device/settings support + flexibility:**

*   Previously, the variants of the USCM were each best-suited to particular controller input types/settings (keyboard-and-mouse vs gamepad devices, Standard vs Classic controls in the game options, etc). Now ALL variants will do their best to support all such combinations of controller, and as such the decision about which variant of the USCM to use will hopefully come down to which in-game actions it maps to the features provided, and how well you can make that work for you with the button mappings configured for your device of choice.
    *   The main factor in achieving this is that now any feature triggers that relies on dection of forward/backward/strafeleft/straferight movement will ALWAYS be able to detect these actions regardless of whether they are performed by a keyboard or a gamepad (different code was previously used for detecting each, and previous versions of the USCM only checked one such approach depending on which variant of the USCM it was).

#### Ported from VC-engine USCM (v6b)

**USCM Variants:**

*   Brought across the "Streamlined Alternate" variant to the SA USCM - it started its life as the 'Gamepad B' variant in VC USCM v6b (an attempt to provide a fully-featured variant for gamepad stunters), and as of v7 it is called "Streamlined Alternate" (like all variants now I have removed the input-method-specific naming as the code is now more supportive of all input methods regardless of variant - see above).

[6\. Known Issues / Quirks](# "Show/Hide associated details")
-------------------------------------------------------------

### Issues

*   Water Respawn, when used in a map-mod without any paths, doesn't take its "alternate" approach of triggering vehicle-exit + jetpack, instead it just always teleports to the same random location every single time, no matter where on the map it was triggered from
    *   _workaround: the issue may be that the mod indeed doesn't have "working paths", but still has some non-working ones defined, and as such the USCM can only assume they are reliable (even if they are not) and try to use them via the "primary" approach. If this is indeed the case, it is possible to edit your game files to ensure it disregards these non-working paths, via editing your "gta\_vc.dat" file and removing a line that mentions "paths.ipl" (please make a backup of your file before doing this)._
*   The Default variant uses ChangeCamera for jetpack activation AND as part of a combination to toggle Frozen Time As a result, it is possible to accidentally activate/deactivate jetpack while trying to toggle Frozen Time
    *   _workaround: when pressing the buttons for the Frozen Time toggle, begin by holding the other button (Crouch) first_
    *   _other approach: customise the scm to change the assigned actions of either feature_
*   While jetpacking, a feature that requires Crouch + Sprint (Ghost Town, in the Default variant; Frozen Time, in the Streamlined Default variants) would take priority over an attempt to 'go down, slowly', which also uses the same button combination. This is an issue a result of the recent addition to make all on-foot controls available while jetpacking (as well as the addition of the 'slow' jetpacking mode).
    *   _workaround: dont try to 'go down, slowly', while jetpacking. sorry_
    *   _other approach: customise the scm to change some/all of the conflicting actions required for the features_
*   Depending on the map-mod/total-conversion-mod the USCM code is used for, some of the cars spawned by the Vehicle Spawner Set features, or the Spawn Random Vehicle feature, may not have been meant for use in that mod. Hopefully at least they wont break the game by their spawning, but that may be dependant on the mods in question.
    *   _workaround: customise the scm to adjust vehicle spawns as necessary_

### Quirks (game-related, not USCM-specific)

*   The "Conversation Yes" and "Conversation No" (referred to as Talk Yes/No elsewhere in this document) in-game actions have a special behaviour that makes them differ from anything else: they are explicitly defined/customisable in the "On Foot" Controls menu, and yet they can also be used (via those same assigned buttons) while the player is in a vehicle.  
      
    This behaviour is loosely implied by the game for "Yes": when in the "In Vehicle" Controls menu, you will see an entry for "Trip Skip" and it will share the exact same buttons you have mapped to "Yes" via the "On Foot" Controls menu. These two actions thus have their assigned buttons completely synchronised - change one and you will see the other change along with it. There is no such equivalent however for "No".  
      
    As a result of this, not only are these two actions available (via the same mapped buttons) both while on-foot and in-vehicle, but also it is possible to define another in-vehicle action to the same button(s) already assigned to these. Normally this sort of button conflict is not allowed by the game, but it will accept it for these two actions. If you go ahead and assign a button to (for example) "Yes" and some other in-vehicle action, then it is the case that pressing that button during gameplay will result in both actions triggering (and doing so will count towards any triggers for USCM features that involve either of the actions).
*   _(Keyboard users only, and possibly also dependant on hardware/driver/OS settings)_  
    If your control mapping leads to having a feature that requires pressing SHIFT and a Numpad-number-button at the same time, it is possible (again, this may not happen to everyone, but I have experienced it) that the game wont trigger the associated USCM feature if both keys are pressed at the same time, nor if the SHIFT is pressed/held first, and rather it will only work if the Numpad-number-button is pressed/held first. If experienced, it is possible that this can be rectified by having NumLock turned off, alternatively changing your mappings such that a different button can be pressed in-place of one of them. (If the issue is indeed also related to hardware/driver/OS then other such solutions may be available; though in my case despite the same USCM variant and control mappings, I only experience this issue in San Andreas and not while playing Vice City).

[7\. Modifying the USCM](# "Show/Hide associated details")
----------------------------------------------------------

### Modification Overview

*   Want to change the action/buttons used to activate a Feature to something more convenient for you?
*   Want to remove a Feature altogether because you don't need it and it just gets in the way?
*   Want to change/reverse the default state of a Feature?
*   Want the Vehicle Spawners to spawn different vehicles?
*   Want to use the USCM in a different San Andreas game-engine map-mod/total-conversion?
*   (etc)

If you are willing to dive into a bit of "scm" coding, you can customise the USCM code to achieve any of these goals. The source code for each USCM variant has been included in this package to attempt to assist this process.

### Source Code Introduction

The source code provided in this package was written in the syntax of, and using the, "Sanny Builder 3.5.1" IDE. It takes advantage of Sanny Builder's support for using TRUE/FALSE as keywords to represent integers 1/0 respectively, and utilises some advantages offered by its "Conditions Check" option (simpler condition type definitions, eg "if and" and "if or", but does not adopt its options for more advanced conditional logic), but otherwise sticks to a non-IDE-specific SCM syntax as much as possible, which incorporates the "opcodes" on every line (thus keeping the "Write Opcodes" option checked, and not using some of the class-based alternatives for certain opcodes).

The source code should thus be compatible with Sanny Builder IDE, but may not necessarily be with any other SCM de/compilers available (eg. BW's Vice Mission Builder). However, the compiled "scm" files included in this package \*will\* be able to be decompiled into editable source code via any such program. In taking this approach you would lose the significant documentation that is present in my included source code (comments, variable names, label names, etc), but all the important USCM logic/functionality would still be present (and in that case, the nicer source code provided in this package could still be used for reference).

### Source Code Context

The bundled source code does not include the raw source of the entire "scm" file, rather it includes only the extracted section of core USCM logic and functionality, which, in a complete `main.scm` file, is surrounded by other unrelated game/map-mod specific "scm" code.

The source code (which, not counting comments, begins with a label, followed by the '03A4: name\_thread "ULTSCM"' line) generally resides in an "scm" file just before the chunk of code for "Mission 0" (if present). The most important single line of code outside of this extracted source code is the one which activates it - that is, a "004F: create\_thread @ULTSCM" line (the label included in this line being the same one the USCM-specific code begins with), which should reside early in the "scm" file in its "MAIN" code chunk (thread), usually among a number of other such lines located in that area of the file.

For more information regarding scm coding syntax and how to modify the USCM, please refer to any documentation included with the editor you decide to use, and look at the comments provided in the source code provided - I have tried my best to ensure that it is as easy-to-follow/understand as possible, including comments to explain many included behaviours/concepts.

[8\. Credits/Acknowledgements](# "Show/Hide associated details")
----------------------------------------------------------------

Mod created by: Dannye

With the support of: Kaneda, M3rrix, Nitzkit, .::bj070893::., Turtle Dick, Buzzsaw, Xtramus, Aries, Psycho, Rainbow, Kingjad, Haywire, Demo00n, Sheeptea, Ltab, Przemoo.

Thanks also to: [the GTAStunting.com forums](https://www.gtastunting.net/index.php?action=forums) and all its members. If you need any support/assistance for this mod please visit [the associated thread](https://www.gtastunting.net/index.php?topic=9046) on that forum.

If you are going to redistribute a copy/customised-version of this mod, please consider including this documentation file (modified as necessary) so users have the all necessary information to assist in using it.

This is the latest release of the mod as of: April 2023.

[Return to top](#top "Return to top")

## gtastunting-essentials
### TO-DO:
- [ ] Add table of commands
- [ ] Add "jump to" links