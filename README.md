# PROJECT IS CURRENTLY (slowly, but surely, sometimes, maybe?) MAINTAINED!!!

---

# L4D2 Survivor Bot AI Improver
A SourceMod plugin for Left 4 Dead 2 that tries to improve the behavior of Survivor Bots as much as possible without giving them a huge cheat-like advantages

---

## Notable Features
- Bots now properly approach their melee target and switch between normal swings and bashing + ability for them to use chainsaws.
- Bots can now pickup and use Tier 3 weapons without having to modify weapon scripts via addons and plugins.
- You can set the weapon preferences for each survivor type (Coach, Zoey, etc.) using the "ib_pref_\*" convars in the game console or plugin's config.
- If enabled, bots that are near witches will slowwalk if the witch isn't close to become enraged.
- If enabled, when the survivor team has too many same types of grenades or sub-types of weapons, they will swap their to the one that isn't.
- Improved and configurable item scavenging system
- Bots now avoid moving through areas that are covered in spit or fire and try to find another way to get to their destination. They also react faster to getting spit under them and escape much efficiently.
- Bots will try to dodge the chargin' chargers and tank's rock that are thrown at them.
- If enabled, bots now can deploy ammopacks if they have any primary weapon and defib dead survivors if they can.
- Bots with shotguns will switch to their pistols if the target is too far away from them. Also, bots with sniper rifles now don't switch to pistols if target is close to them.
- If enabled, bots with pump shotguns and CSS sniper rifles can shove upon firing to boost their firerate.
- Bots shouldn't now completely ignore targets that are directly behind them and shoot at witch's feet at close range.
- If the optional Actions extension is installed, bots shouldn't now try to save a survivor if tanks are near them
- Bots can now throw grenades at huge mob and tanks.
- And other features that I forgot about due to too much work. Many of the features above can be disabled or tweaked in the config file.
---
### Notable Differences (blatantly copied from [Kerouha's currently unmaintained fork](https://github.com/Kerouha/L4D2-Survivor-Bot-AI-Improver/tree/experimental))
- Bots will fire upon staggered Witch before she targets anyone ([video](https://youtu.be/jGsh1iDgqBw?t=11))
- To resolve massive slowdowns in certain places (like when bots' path to wanted item is nav_blocked), function that calculates distance from a bot to an object was changed.
- Bots are less likely commit absurd backtracking (or deviate far from main path) to grab items. Takes `ib_grab_distance`/`ib_grab_visible_distance` into account. Range is reduced depending on bot's health and amount of threats around.
- Bots are less likely to grab items from unrealistic distance, or through doors/walls. See `ib_grab_pickup_distance`.
- Reduced string operations to a minimum, at least when it comes to inventory management. This *should* give better performance, right?
- Previously, you could experience following behavior: when someone gets downed, bot could snatch their secondary weapon, resulting in incapacitated player having no secondary upon being revived. This is fixed.
- `ib_t3_refill` – allow bots to pick up ammo when carrying a Tier 3 weapon ([if your server has this feature](https://github.com/LuxLuma/-L4D2-M60_GrenadeLauncher_patches))
- `ib_ammotype_override` – if your server has weapons with modified ammo types/capacity, put them in a format: `weapon_id:ammo_max weapon_id:ammo_max ...` Shouldn't be needed if weapon uses it's default ammo type. See weapon IDs [here](https://github.com/SilvDev/Left4DHooks/blob/e10791726db1d18818ed23faa6878fcfeeb4845f/sourcemod/scripting/include/left4dhooks_stocks.inc#L1543).
- Some commands and functions to test stuff
- CVar names changed and shortened for convenience

---

## Requirements
- **MetaMod:Source 1.11 or higher:** https://www.sourcemm.net/downloads.php?branch=stable
- **SourceMod 1.12:** https://www.sourcemod.net/downloads.php?branch=stable
- **Left 4 DHooks Direct:** https://forums.alliedmods.net/showthread.php?t=321696
- **Actions (Optional - Fixes bots always rushing to save their incapped friend or stopping to retreat in tank battle ):** https://forums.alliedmods.net/showpost.php?p=2771520&postcount=1

---

## Installation
1. Download the files in the Requirements section;
2. Extract the files from SourceMod and MetaMod's archives inside your game folder (Ex. C:\Program Files (x86)\Steam\steamapps\common\Left 4 Dead 2\left4dead2);
3. Extract the "sourcemod" folder from Left 4 DHooks Direct inside the "addons" folder;
4. If you chose to install Actions, extract the folders inside the archive to the "addons/sourcemod/" folder;
5. Download the zip file of this repository;
6. Put the "gamedata", "plugins", "data", and "scripting" folders inside "addons/sourcemod".

---

## Note for Left 4 Bots 2 Users
If you're gonna use this plugin alongside [Left 4 Bots 2](https://steamcommunity.com/sharedfiles/filedetails/?id=3022416274) addon, the make sure to change some of its settings (located in "<game folder>/left4dead2/ems/left4bots2/cfg") so that it doesn't conflict with the plugin's:
- Inside "weapons" folder, you'll find the addon's weapons preferences for each survivor. Open each text file with any editor and make sure that the lines with written weapons and items start with "\*,". For example:
	- \*,sniper_military,hunting_rifle,rifle_ak47,rifle_sg552,rifle,rifle_desert,autoshotgun,shotgun_spas,rifle_m60,grenade_launcher,sniper_scout,sniper_awp,smg,smg_silenced,smg_mp5,shotgun_chrome,pumpshotgun
	- \*,pistol_magnum,pistol,chainsaw,machete,golfclub,katana,fireaxe,crowbar,cricket_bat,baseball_bat,tonfa,shovel,electric_guitar,knife,frying_pan,pitchfork,riotshield
	- \*,molotov,pipe_bomb,vomitjar
	- \*,first_aid_kit,defibrillator,upgradepack_incendiary,upgradepack_explosive
	- \*,pain_pills,adrenaline
- In "settings.txt" or any text files inside that begins with it, change the listed settings to following:
	- dodge_charger = 0
	- dodge_rock = 0
	- dodge_spit = 0
	- shoot_rock = 0
	- spit_block_nav = 0
	- If you want to use this plugin's upgrade deploy feature (which currently is very WIP):
		- deploy_upgrades = 0
	- If you ever going to set some survivor's preference in this plugin to secondary weapon only:
		- enforce_shotgun = 0
		- enforce_sniper_rifle = 0
	- If you want to use this plugin's grenade throw feature:
		- throw_molotov = 0
		- throw_pipebomb = 0
		- throw_vomitjar = 0

---

## Configuration Settings
Config file is created after starting any campaign with plugin enabled at least once and is located in "(Game installation path)/left4dead2/cfg/sourcemod/l4d2_improved_bots.cfg"

```
// If your server has weapons with modified ammo types/amounts, put them here in a following format: "weapon_id:ammo_max weapon_id:ammo_max ..."
// -
// Default: ""
ib_ammotype_override ""

// Makes survivor bots automatically shove every nearby infected. <0: Disabled, 1: All infected, 2: Only if infected is behind them>
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "2.000000"
ib_autoshove_enabled "1"

// If bots should change their primary weapon to other one if they're using CSS weapons.
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_avoid_css "0"

// (WIP) If bots should avoid and retreat from tanks that are nearby punchable props (like cars).
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_avoidtanksnearpunchableprops "0"

// Spam console/chat in hopes of finding a a clue for your problems. Prints WILL LAG on Windows GUI!
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1024.000000"
ib_debug "0"

// Range at which survivor's dead body should be for bot to consider it reviveable.
// -
// Default: "2000"
// Minimum: "0.000000"
ib_defib_revive_distance "2000"

// Enable bots reviving dead players with defibrillators if they have one available.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_defib_revive_enabled "1"

// (WIP) If bots should deploy their upgrade pack when available and not in combat.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_deployupgradepacks "1"

// If bots shouldn't switch to their pistol while they have sniper rifle equipped.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_dontswitchtopistol "1"

// Enables survivor bots's charger dodging behavior.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_evade_charge "1"

// Enables survivor bots' improved spitter acid evasion
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_evade_spit "1"

// Distance at which a not visible item should be for bot to move it.
// -
// Default: "300"
// Minimum: "0.000000"
ib_grab_distance "300"

// Enable improved bot item scavenging for specified items.
// <0: Disabled, 1: Pipe Bomb, 2: Molotov, 4: Bile Bomb, 8: Medkit, 16: Defib, 32: UpgradePack, 64: Pills, 128: Adrenaline, 256: Laser Sights, 512: Ammopack, 1024: Ammopile, 2048: Chainsaw, 4096: Secondary Weapons, 8192: Primary Weapons. Add numbers together>
// -
// Default: "16383"
// Minimum: "0.000000"
// Maximum: "16383.000000"
ib_grab_enabled "16383"

// How close should the item be to the survivor bot to able to count it when searching?
// -
// Default: "2000"
// Minimum: "0.000000"
ib_grab_mapsearchdistance "2000"

// If enabled, objects with certain models will be considered as scavengeable items.
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_grab_models "0"

// The bots' scavenge distance is multiplied to this value when there's no human players left in the team.
// -
// Default: "2.5"
// Minimum: "0.000000"
ib_grab_nohumans_rangemultiplier "2.5"

// Distance at which item should be for bot to able to pick it up.
// -
// Default: "90"
// Minimum: "0.000000"
ib_grab_pickup_distance "90"

// Distance at which a visible item should be for bot to move it.
// -
// Default: "600"
// Minimum: "0.000000"
ib_grab_visible_distance "600"

// Enables survivor bots throwing grenades.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_gren_enabled "1"

// Infected count required to throw grenade Multiplier (Value * SurvivorCount).
// -
// Default: "5.0"
// Minimum: "1.000000"
ib_gren_horde_size_multiplier "5.0"

// Second number to pick to randomize next grenade throw time.
// -
// Default: "35"
// Minimum: "0.000000"
ib_gren_next_throw_time_max "35"

// First number to pick to randomize next grenade throw time.
// -
// Default: "15"
// Minimum: "0.000000"
ib_gren_next_throw_time_min "15"

// Range at which target needs to be for bot to throw grenade at it.
// -
// Default: "1500"
ib_gren_throw_range "1500"

// What grenades should survivor bots throw? <1: Pipe-Bomb, 2: Molotov, 4: Bile Bomb. Add numbers together.>
// -
// Default: "7"
// Minimum: "1.000000"
// Maximum: "7.000000"
ib_gren_types "7"

// If the survivor bot's primary ammo percentage is above this value, they'll consider that they have enough ammo before refill
// -
// Default: "0.33"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_hasenoughammo_ratio "0.33"

// Makes survivor bots force attack pinned survivor's SI if possible. <0: Disabled, 1: Shoot at attacker, 2: Shove the attacker if close enough. Add numbers together.>
// -
// Default: "3"
// Minimum: "0.000000"
// Maximum: "3.000000"
ib_help_pinned_enabled "3"

// Range at which bots will start firing at SI.
// -
// Default: "1000"
// Minimum: "0.000000"
ib_help_pinned_shootrange "1000"

// Range at which bots will start to bash SI.
// -
// Default: "75"
// Minimum: "0.000000"
ib_help_pinned_shoverange "75"

// Range at which bot's target should be to start taking aim at it.
// -
// Default: "125"
// Minimum: "0.000000"
ib_melee_aim_range "125"

// Range at which bot's target should be to approach it. <0: Disable Approaching>
// -
// Default: "125"
// Minimum: "0.000000"
ib_melee_approach_range "125"

// Range at which bot's target should be to start attacking it.
// -
// Default: "75"
// Minimum: "0.000000"
ib_melee_attack_range "75"

// The total number of chainsaws allowed on the team. <0: Bots never use chainsaw>
// -
// Default: "1"
// Minimum: "0.000000"
ib_melee_chainsaw_limit "1"

// The nearby infected count required for bot to switch to chainsaw.
// -
// Default: "8"
// Minimum: "1.000000"
ib_melee_chainsaw_switch_count "8"

// Enables survivor bots' improved melee behaviour.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_melee_enabled "1"

// The total number of melee weapons allowed on the team. <0: Bots never use melee>
// -
// Default: "2"
// Minimum: "0.000000"
ib_melee_max_team "2"

// Chance for bot to bash target instead of attacking with melee. <0: Disable Bashing>
// -
// Default: "3"
// Minimum: "0.000000"
ib_melee_shove_chance "3"

// The nearby infected count required for bot to switch to their melee weapon.
// -
// Default: "4"
// Minimum: "1.000000"
ib_melee_switch_count "4"

// Range at which bot's target should be to switch to melee weapon.
// -
// Default: "200"
// Minimum: "0.000000"
ib_melee_switch_range "200"

// Makes survivor bots change their grenade type if there's too much of the same one, Ex. Pipe-Bomb to Molotov.
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_mix_grenades "0"

// Makes survivor bots change their primary weapon subtype if there's too much of the same one, Ex. change AK-47 to M16 or SPAS-12 to Autoshotgun.
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_mix_primaries "0"

// Enable if you're playing on NIGHTMARE modpack! Adjusts the bot's behaviors to fit better to it
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_nightmare "0"

// If enabled, survivor bots won't take fall damage if they were climbing a ladder just before that.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_nofalldmgonladderfail "1"

// Bot Bill's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "5.000000"
ib_pref_bill "1"

// Bot Coach's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "2"
// Minimum: "0.000000"
// Maximum: "5.000000"
ib_pref_coach "2"

// Bot Ellis's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "3"
// Minimum: "0.000000"
// Maximum: "5.000000"
ib_pref_ellis "3"

// Bot Francis's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "2"
// Minimum: "0.000000"
// Maximum: "5.000000"
ib_pref_francis "2"

// Bot Louis's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "5.000000"
ib_pref_louis "1"

// If every survivor bot should only use magnum instead of regular pistol if possible.
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_pref_magnums_only "0"

// Bot Nick's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "5.000000"
ib_pref_nick "1"

// Bot Rochelle's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "5.000000"
ib_pref_rochelle "1"

// Bot Zoey's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "3"
// Minimum: "0.000000"
// Maximum: "5.000000"
ib_pref_zoey "3"

// Bots' data computing time delay (infected count, nearby friends, etc). Increasing the value might help increasing the game performance, but slow down bots.
// -
// Default: "0.1"
// Minimum: "0.033000"
ib_process_time "0.1"

// Enables survivor bots shooting tank's thrown rocks.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_shootattankrocks_enabled "1"

// Range at which rock needs to be for bot to start shooting at it.
// -
// Default: "1000"
// Minimum: "0.000000"
ib_shootattankrocks_range "1000"

// Chance at which survivor bot may shove after firing a bolt-action sniper rifle. <0: Disabled, 1: Always>
// -
// Default: "0"
// Minimum: "0.000000"
ib_shove_chance_css "0"

// Chance at which survivor bot may shove after firing a pump-action shotgun. <0: Disabled, 1: Always>
// -
// Default: "0"
// Minimum: "0.000000"
ib_shove_chance_pump "0"

// The total number of grenade launchers allowed on the team. <0: Bots never use grenade launcher>
// -
// Default: "0"
// Minimum: "0.000000"
ib_t3_limit_gl "0"

// The total number of M60s allowed on the team. <0: Bots never use M60>
// -
// Default: "1"
// Minimum: "0.000000"
ib_t3_limit_m60 "1"

// Should bots pick up ammo when carrying a Tier 3 weapon? Keep disabled if your server does not allow that. <0: Disabled, 1: Grenade Launcher, 2: M60, 3: Both>
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "3.000000"
ib_t3_refill "0"

// If bots should take cover from tank's thrown rocks.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_takecoverfromtankrocks "1"

// Enables survivor bots' improved target selection.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_targeting_enabled "1"

// If bots shouldn't target common infected that are currently not attacking survivors.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
ib_targeting_ignoredociles "1"

// Range at which target need to be for bots to start firing at it.
// -
// Default: "1500"
// Minimum: "0.000000"
ib_targeting_range "1500"

// Range at which target need to be for bots to start firing at it with secondary weapon.
// -
// Default: "1000"
// Minimum: "0.000000"
ib_targeting_range_pistol "1000"

// Range at which target need to be for bots to start firing at it with shotgun.
// -
// Default: "800"
// Minimum: "0.000000"
ib_targeting_range_shotgun "800"

// Range at which target need to be for bots to start firing at it with sniper rifle.
// -
// Default: "2500"
// Minimum: "0.000000"
ib_targeting_range_sniperrifle "2500"

// The field of view of survivor bots.
// -
// Default: "75.0"
// Minimum: "0.000000"
// Maximum: "180.000000"
ib_vision_fov "75.0"

// The time required for bots to notice enemy target is multiplied to this value.
// -
// Default: "1.1"
// Minimum: "0.000000"
// Maximum: "4.000000"
ib_vision_noticetimescale "1.1"

// (WIP) Allows survivor bots to crown witch on their path if they're holding any shotgun type weapon. <0: Disabled; 1: Only if survivor team doesn't have any human players; 2:Enabled>
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "2.000000"
ib_witchbehavior_allowcrowning "0"

// Survivor bots will start walking near witch if they're this range near her and she's not disturbed. <0: Disabled>
// -
// Default: "0"
// Minimum: "0.000000"
ib_witchbehavior_walkwhennearby "0"
```
