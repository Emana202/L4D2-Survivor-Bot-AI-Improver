# PROJECT IS CURRENTLY UNMAINTAINED;

---

# L4D2 Survivor Bot AI Improver
A SourceMod plugin for L4D2 trying to improve survivor bots' AI as much as possible

---

## Notable features
- Better melee weapon handling and usage
- Usage of Tier 3 weapons and Chainsaws without modifying weapon scripts
- Configurable weapon preference for each survivor type
- Improved and configurable item scavenging system
- Faster spitter acid evasion
- Charger charge dodging
- Deployment of upgradepacks 
- Defibing death survivors
- Better infected target selection
- Fixed AI behavior when battling with tank and witch
- Grenade throwing
- And many other features...

---

## Requirements
- **MetaMod:Source 1.11 or higher:** https://www.sourcemm.net/downloads.php?branch=stable
- **SourceMod 1.11 or higher:** https://www.sourcemod.net/downloads.php?branch=stable
- **Left 4 DHooks Direct:** https://forums.alliedmods.net/showthread.php?t=321696
- **Actions (Optional - Fixes bots always rushing to save their incapped friend or stopping to retreat in tank battle ):** https://forums.alliedmods.net/showpost.php?p=2771520&postcount=1

---

## Installation
1. Download the files in the Requirements section;
2. Extract the files from SourceMod and MetaMod's archives inside your game folder (Ex. C:\Program Files (x86)\Steam\steamapps\common\Left 4 Dead 2\left4dead2);
3. Extract the "sourcemod" folder from Left 4 DHooks Direct inside the "addons" folder;
4. If you chose to install Actions, extract the folders inside the archive to the "addons/sourcemod/" folder;
5. Download the zip file of this repository;
6. Put the "gamedata", "plugins", and "scripting" folders inside "addons/sourcemod".

---

## Configuration Settings
Config file is created after starting any campaign with plugin enabled at least once and is located in "(Game installation path)/left4dead2/cfg/sourcemod/l4d2_improved_bots.cfg"

```
// If survivor bot shouldn't drop his currently carrying prop no matter what.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_alwayscarryprop "1"

// Makes survivor bots automatically shove every nearby infected. <0: Disabled, 1: All infected, 2: Only if infected is behind them>
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "2.000000"
l4d2_improvedbots_autoshove_enabled "1"

// Makes survivor bots change their grenade type if there's too much of the same one, Ex. Pipe-Bomb to Molotov.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_changeweaponiftoomanysubtype_grenades "1"

// Makes survivor bots change their primary weapon subtype if there's too much of the same one, Ex. change AK-47 to M16 or SPAS-12 to Autoshotgun.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_changeweaponiftoomanysubtype_primaries "1"

// Enables survivor bots's charger dodging behavior.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_chargerevasion "1"

// Range at which survivor's dead body should be for bot to consider it reviveable.
// -
// Default: "2000"
// Minimum: "0.000000"
l4d2_improvedbots_defib_revive_distance "2000"

// Enable bots reviving dead players with defibrillators if they have one available.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_defib_revive_enabled "1"

// If bots should deploy their upgrade pack when available and not in combat.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_deployupgradepacks "1"

// If bots shouldn't switch to their pistol while they have sniper rifle equiped.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_dontswitchtopistol "1"

If bots should take cover from tank's thrown rocks.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_takecoverfromtankrocks "1"

// If bots should avoid and retreat from tanks that are nearby punchable props like cars.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_avoidtanksnearpunchableprops "1"

// Enables survivor bots' improved spitter acid evasion
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_evadespitteracids "1"

// The field of view of survivor bots.
// -
// Default: "60.0"
// Minimum: "0.000000"
// Maximum: "180.000000"
l4d2_improvedbots_vision_fieldofview "60.0"

// The time required for bots to notice enemy target is multiplied to this value.
// -
// Default: "1.0"
// Minimum: "0.000000"
// Maximum: "4.000000"
l4d2_improvedbots_vision_noticetimescale "1.0"

// Chance at which survivor bot may shove after firing a bolt-action sniper rifle. <0: Disabled, 1: Always>
// -
// Default: "3"
// Minimum: "0.000000"
l4d2_improvedbots_fireshove_chance_css_sniperrifles "3"

// Chance at which survivor bot may shove after firing a pump-action shotgun. <0: Disabled, 1: Always>
// -
// Default: "4"
// Minimum: "0.000000"
l4d2_improvedbots_fireshove_chance_pumpshotguns "4"

// Enables survivor bots throwing grenades.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_grenadethrowing_enabled "1"

// What grenades should survivor bots throw? <1: Pipe-Bomb, 2: Molotov, 4: Bile Bomb. Add numbers together.>
// -
// Default: "7"
// Minimum: "1.000000"
// Maximum: "7.000000"
l4d2_improvedbots_grenadethrowing_grenadetypes "7"

// Infected count required to throw grenade Multiplier (Value * SurvivorCount).
// -
// Default: "3.75"
// Minimum: "1.000000"
l4d2_improvedbots_grenadethrowing_horde_size_multiplier "3.75"

// Second number to pick to randomize next grenade throw time.
// -
// Default: "30"
// Minimum: "0.000000"
l4d2_improvedbots_grenadethrowing_next_throw_time_max "30"

// First number to pick to randomize next grenade throw time.
// -
// Default: "20"
// Minimum: "0.000000"
l4d2_improvedbots_grenadethrowing_next_throw_time_min "20"

// Range at which target needs to be for bot to throw grenade at it.
// -
// Default: "1000"
l4d2_improvedbots_grenadethrowing_throw_range "1000"

// Makes survivor bots force attack pinned survivor's SI if possible. <0: Disabled, 1: Shoot at attacker, 2: Shove the attacker if close enough. Add numbers together.>
// -
// Default: "3"
// Minimum: "0.000000"
// Maximum: "3.000000"
l4d2_improvedbots_help_pinnedfriend_enabled "3"

// Range at which bots will start firing at SI.
// -
// Default: "2000"
// Minimum: "0.000000"
l4d2_improvedbots_help_pinnedfriend_shootrange "2000"

// Range at which bots will start to bash SI.
// -
// Default: "75"
l4d2_improvedbots_help_pinnedfriend_shoverange "75"

// Enable improved bot item scavenging for specified items. <0: Disable, 1: Pipe Bomb, 2: Molotov, 4: Bile Bomb, 8: Medkit, 16: Defibrillator, 32: UpgradePack, 64: Pain Pills, 128: Adrenaline, 256: Laser Sights, 512: Ammopack, 1024: Ammopile, 2048: Chainsaw
// -
// Default: "16383"
// Minimum: "0.000000"
// Maximum: "16383.000000"
l4d2_improvedbots_itemscavenge_enabled "16383"

// The bots' scavenge distance is multiplied to this value when there's no human players left in the team.
// -
// Default: "3.0"
// Minimum: "0.000000"
l4d2_improvedbots_itemscavenge_nohumans_rangemultiplier "3.0"

// Distance at which item should be for bot to able to pick it up.
// -
// Default: "96"
// Minimum: "0.000000"
l4d2_improvedbots_itemscavenge_pickup_distance "96"

// Distance at which item should be for bot to move it.
// -
// Default: "300"
// Minimum: "0.000000"
l4d2_improvedbots_itemscavenge_scavenge_distance "300"

// Distance at which a visible item should be for bot to move it.
// -
// Default: "600"
// Minimum: "0.000000"
l4d2_improvedbots_itemscavenge_scavenge_visible_distance "600"

// If bots shouldn't stop moving in combat when there's no human players in team.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_keepmovingincombat "1"

// Range at which bot's target should be to start taking aim at it.
// -
// Default: "125"
// Minimum: "0.000000"
l4d2_improvedbots_melee_aim_range "125"

// Range at which bot's target should be to approach it. <0: Disable Approaching>
// -
// Default: "500"
// Minimum: "0.000000"
l4d2_improvedbots_melee_approach_range "500"

// Range at which bot's target should be to start attacking it.
// -
// Default: "70"
// Minimum: "0.000000"
l4d2_improvedbots_melee_attack_range "70"

// The total number of chainsaws allowed on the team. <0: Bots never use chainsaw>
// -
// Default: "1"
// Minimum: "0.000000"
l4d2_improvedbots_melee_chainsaw_limit "1"

// The nearby infected count required for bot to switch to chainsaw.
// -
// Default: "6"
// Minimum: "1.000000"
l4d2_improvedbots_melee_chainsaw_switch_count "6"

// Enables survivor bots' improved melee behaviour.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_melee_enabled "1"

// The total number of melee weapons allowed on the team. <0: Bots never use melee>
// -
// Default: "1"
// Minimum: "0.000000"
l4d2_improvedbots_melee_max_team "1"

// Chance for bot to bash target instead of attacking with melee. <0: Disable Bashing>
// -
// Default: "4"
// Minimum: "0.000000"
l4d2_improvedbots_melee_shove_chance "4"

// The nearby infected count required for bot to switch to their melee weapon.
// -
// Default: "3"
// Minimum: "1.000000"
l4d2_improvedbots_melee_switch_count "3"

// Range at which bot's target should be to switch to melee weapon.
// -
// Default: "300"
// Minimum: "0.000000"
l4d2_improvedbots_melee_switch_range "300"

// Bots' data computing time delay (infected count, nearby friends, etc). Increasing the value might help increasing the game performance, but slow down bots.
// -
// Default: "0.1"
// Minimum: "0.033000"
l4d2_improvedbots_process_time "0.1"

// Enables survivor bots shooting tank's thrown rocks.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_shootattankrocks_enabled "1"

// Range at which rock needs to be for bot to start shooting at it.
// -
// Default: "1500"
// Minimum: "0.000000"
l4d2_improvedbots_shootattankrocks_range "1500"

// If bots should change their primary weapon to other one if they're using CSS weapons.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_switchoffcssweapon "1"

// Enables survivor bots' improved target selection.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_targetselection_enabled "1"

// If bots shouldn't target common infected that are currently not attacking survivors.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_targetselection_ignoredociles "1"

// Range at which target need to be for bots to start firing at it.
// -
// Default: "2000"
// Minimum: "0.000000"
l4d2_improvedbots_targetselection_shootrange "2000"

// Range at which target need to be for bots to start firing at it with secondary weapon.
// -
// Default: "1500"
// Minimum: "0.000000"
l4d2_improvedbots_targetselection_shootrange_pistol "1500"

// Range at which target need to be for bots to start firing at it with shotgun.
// -
// Default: "750"
// Minimum: "0.000000"
l4d2_improvedbots_targetselection_shootrange_shotgun "750"

// Range at which target need to be for bots to start firing at it with sniper rifle.
// -
// Default: "3000"
// Minimum: "0.000000"
l4d2_improvedbots_targetselection_shootrange_sniperrifle "3000"

// The total number of grenade launchers allowed on the team. <0: Bots never use grenade launcher>
// -
// Default: "1"
// Minimum: "0.000000"
l4d2_improvedbots_tier3weaponlimit_grenadelauncher "1"

// The total number of M60s allowed on the team. <0: Bots never use M60>
// -
// Default: "1"
// Minimum: "0.000000"
l4d2_improvedbots_tier3weaponlimit_m60 "1"

// Bot Bill's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "5.000000"
l4d2_improvedbots_weapon_preference_bill "1"

// Bot Coach's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "2"
// Minimum: "0.000000"
// Maximum: "5.000000"
l4d2_improvedbots_weapon_preference_coach "2"

// Bot Ellis's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "3"
// Minimum: "0.000000"
// Maximum: "5.000000"
l4d2_improvedbots_weapon_preference_ellis "3"

// Bot Francis's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "2"
// Minimum: "0.000000"
// Maximum: "5.000000"
l4d2_improvedbots_weapon_preference_francis "2"

// Bot Louis's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "5.000000"
l4d2_improvedbots_weapon_preference_louis "1"

// If every survivor bot should only use magnum instead of regular pistol if possible.
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
l4d2_improvedbots_weapon_preference_magnums_only "0"

// Bot Nick's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "5.000000"
l4d2_improvedbots_weapon_preference_nick "1"

// Bot Rochelle's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "5.000000"
l4d2_improvedbots_weapon_preference_rochelle "1"

// Bot Zoey's weapon preference. <0: Default, 1: Assault Rifle, 2: Shotgun, 3: Sniper Rifle, 4: SMG, 5: Secondary Weapon>
// -
// Default: "3"
// Minimum: "0.000000"
// Maximum: "5.000000"
l4d2_improvedbots_weapon_preference_zoey "3"

// Allows survivor bots to crown witch on their path if they're holding any shotgun type weapon. <0: Disabled; 1: Only if survivor team doesn't have any human players; 2:Enabled>
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "2.000000"
l4d2_improvedbots_witchbehavior_allowcrowning "1"

// Survivor bots will start walking near witch if they're this range near her and she's not disturbed. <0: Disabled>
// -
// Default: "500"
// Minimum: "0.000000"
l4d2_improvedbots_witchbehavior_walkwhennearby "500"
```
