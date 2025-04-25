# [Maintenance Mode Merger of Rules](https://steamcommunity.com/sharedfiles/filedetails/?id=2807759164)
[![Stellaris Mod Deploy Action Status](https://github.com/aerolfos/Maintenance_Mode_Merger_of_Rules/actions/workflows/deployStellarisMod.yml/badge.svg)](https://github.com/aerolfos/Maintenance_Mode_Merger_of_Rules/actions/workflows/deployStellarisMod.yml)
[![GitHub Release Badge](https://img.shields.io/github/v/release/aerolfos/Maintenance_Mode_Merger_of_Rules?logo=github&style=flat)](https://github.com/Aerolfos/Maintenance_Mode_Merger_of_Rules/releases/latest)

![Blue Triangle](https://raw.githubusercontent.com/Aerolfos/stellaris_mod_deploy_action/main/assets/blue_caution_triangle.png) Supports Stellaris version: `3.14.x`

This is a community fork of [Inny's Merger of Rules](https://steamcommunity.com/sharedfiles/filedetails/?id=2807759164) mod. The intention is to provide a Github-based collaborative version of the merger, where mod authors can work together to maintain compatibility. Active development other than maintenance (and mod author contributions) has been discontinued.

## Description
The Merger of Rules mod serves as a global compatibility patch for Stellaris, designed to harmonize various incompatible game rules and scripted triggers introduced by different mods.
When two mods alter the same rule or scripted trigger, only the last loaded mod takes effect, potentially causing issues with the earlier mod. The Merger resolves this by ensuring that all relevant rules from multiple mods are applied seamlessly.
In addition to merging game rules, this mod also integrates several common scripted triggers shared by multiple mods, such as `is_megacorp` or capital building triggers. This integration allows for the construction of buildings from different mods, provided you have an equivalent capital on your planet.

Furthermore, the mod includes a shader merge for ACOT/AOT, Gigas, and Real Space, ensuring visual compatibility across these popular mods.

Compatibility is only maintained for mods that have been made for, or updated to the latest version of Stellaris.

You will need the merger of rules if you use more than one of the mods in the following collection:

### -> [Supported Mods for 3.X](https://steamcommunity.com/sharedfiles/filedetails/?id=2604226821) <-

> [!IMPORTANT]
> Make sure to place the Merger at the end of your load order.

## Recommended:
[Universal Resource Patch](https://steamcommunity.com/sharedfiles/filedetails/?id=1595876588)

## Mini-Patches:
These patches are mandatory for support of their related mod.
- [Expanded Events](https://steamcommunity.com/sharedfiles/filedetails/?id=3410671527)
- [Expanded Megastructures and Technologies](https://steamcommunity.com/sharedfiles/filedetails/?id=3410670780)
- [Expanded Traits, Civics, Pops, and More](https://steamcommunity.com/sharedfiles/filedetails/?id=3410670611)
- [Girls Frontline](https://steamcommunity.com/sharedfiles/filedetails/?id=3280119957)
- [Leviathan Events Xtended - Legacy](https://steamcommunity.com/sharedfiles/filedetails/?id=3302382866)
- [Madoka Magica New](https://steamcommunity.com/sharedfiles/filedetails/?id=3410676642)
- [Plentiful Traditions](https://steamcommunity.com/sharedfiles/filedetails/?id=3424044503)
- [Real Space](https://steamcommunity.com/sharedfiles/filedetails/?id=3279553160)
- [Wula Fallen Empire](https://steamcommunity.com/sharedfiles/filedetails/?id=3410670415)

## Incompatible mods
- _Universial Game Rules Patch_
  - You don't need UGRC as MoR covers more mods while making the rules acknowledge the existence of other mods, but if your collection of mods is mainly Chinese, you'll want to use UGRP instead.
- _Various Servant Jobs_ 
  - This will cause habitability bugs.
- _Ethics and Civics Alternative Restored_
  - Has completely messed up policies files.
- _Prime Collective Crisis - Pandora's Star_
  - Causes zero habitability bug.
- _Habitable Structures Patch_
  - Made obsolete since Stellaris 3.0 totally changed how the trigger works. Compatibility now handled by the Merger.
- Any total conversion or global overhaul.
  - Total conversions are by definition incompatible with most other mods. 


## Installation
Steam owners should subscribe to the [Steam Workshop version of the mod](https://steamcommunity.com/sharedfiles/filedetails/?id=2807759164).

[Manual download](https://github.com/Aerolfos/Maintenance_Mode_Merger_of_Rules/releases/latest).

[Manual installation instructions](https://github.com/Aerolfos/stellaris_mod_deploy_action/wiki/Mod-Installation).

## Recommended load order
1. **Ariphaos Unofficial Patch** or **Scripted Trigger Undercoat**
2. <Your mods here, check mod descriptions for specific instructions>
3. <The patch mods come after, they must be able to overwrite the previous mods they're supposed to patch>
4. Universal Resource Patch
5. The Merger of Rules

> [!TIP]
> [See the Paradox Wiki for more information on mod load ordering.](https://stellaris.paradoxwikis.com/Modding#Mod_load_order)

## Troubleshooting
> [!TIP]
> Steam sometimes fails to update mod files correctly. Performing regular integrity checks on the game usually resolves this issue.

# Other Compatibility patches
- [ACOT + Dawn of Ascension -> Acquisition of Technology](https://steamcommunity.com/sharedfiles/filedetails/?id=2178603631)
- [Sartek Tradition - Ascension Perk Merger](https://steamcommunity.com/sharedfiles/filedetails/?id=2821711162)
- [Sartek District and Economy Merger Add-on](https://steamcommunity.com/sharedfiles/filedetails/?id=2877750087)

## Modders: notes for supporting the merger
- Add comments when you overwrite vanilla code, to make it easier to see where the code has changed.
- Favor creating and using scripted triggers whenever you're checking for a list of things, also if you're restricting to some country types.
  Adding compatibility to an event restricted to `country_type = default` requires overwriting the event, but if you used a trigger, it's much easier to overwrite it.
- Write a changelog. This helps a lot more than you might think.
- Concerning ID triggers:
  It's a simple thing - add in your mod a trigger stating for example `trg_my_mod = { always = yes }`
  Other mods that want to check on yours will have a placeholder file set to be easily overwritten and put `trg_my_mod = { always = no }`
  The big advantage over a global flag is that this allows for detection before game start, essential for policies, pop assembly, buildings, etc.
- In addition to a trigger, supplement a variable of the form `@my_mod = 1`, the merger can use this for more advanced conditionals with inlines which helps performance. 
- Trigger+variable completely supersedes using a mod flag. You should prefer those two.

## Other notes for modders
- If you have specific worlds that you don't want to be targeted by planet killers, flag them with `planet_flag = merg_forbidden_target` and the Merger will make sure that, modded or vanilla, they won't break your mod.
  You can also detect the presence of the Merger with the global flag `merged_rules`.

Uses [Stellaris Mod Deploy Action](https://github.com/aerolfos/stellaris_mod_deploy_action), for deployment automation.

## Credits
Original mod: [Merger of Rules by Inny](https://steamcommunity.com/sharedfiles/filedetails/?id=2807759164)

All the actual hard work: Inny

## License
Extra code and documentation by me (Aerolfos) are licensed under [GNU GPL v3.0](LICENSE). Original work on the mod belongs to Inny. Forked with permission.

> [!WARNING]
> You're not allowed to redistribute this mod in whole, with the exception of private multiplayer packs. Do not make private packs publicly accessible.

You can add portions of the code to your own mod, but please notify Inny if you do so.
The above rules don't apply if you fork the Merger to support an overhaul/conversion mod.

This mod is subject to the [Paradox User Agreement](https://legal.paradoxplaza.com/eula), which governs Paradox or Paradox-associated third party assets or material. Specifically,

> Your rights in your UGC only extend to the new, original content you create as part of your UGC and do not extend to or grant any rights to the Services or anything created or made available by third parties, or any content made available by Paradox through the Services.



