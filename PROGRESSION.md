# SENTINEL — Rank, XP, Operator Roles & Ranked Arsenal

Updated for the **SENTINEL V2.04.472 Al Rayak TEST mission**. Latest mission code and release notes determine active role tiers; this is not a claim of dedicated-server acceptance.

Your SENTINEL career moves with the campaign. Military rank, career points, specialization XP and Ranked Arsenal progress continue with you from one deployment to the next.

> **The deployment can change. Your career continues. Your lobby slot assigns your active Operator Role.**

## 1. Career and Operator Role

Your SENTINEL career includes:

- military rank and career points;
- independent specialization XP for every Operator Role;
- Ranked Arsenal progression for each specialization.

The **eight current playable operator role categories** are:

- RECON (Recon JTAC)
- COMBAT_SPECIALIST (Combat Specialist)
- MORTAR (Mortar)
- SNIPER (Sniper)
- ANTI_ARMOR (Anti-Armor / Air Defense)
- HEAVY_GUNNER (Heavy Gunner)
- MEDIC (Medic)
- HELI_PILOT (Helicopter Pilot)

There is **no playable Battle Captain**. Historical Battle Captain and retired-role records remain available internally for save/profile compatibility.

The **multiplayer lobby slot is the sole authority for the active Operator Role**. To change specialization, return to the multiplayer lobby and select a different role slot. The CENTCOM Tablet **OPERATOR ROLE** page is view/status only and does not change your role.

Changing lobby slots does not erase progress already earned in another specialization.

## 2. Career points and rank

Career points (`PTS`) determine military rank.

### Major point sources

| Event | Award / Penalty |
| --- | ---: |
| Countable hostile infantry kill | +1 PTS |
| Eligible hostile static weapon destroyed | +3 PTS |
| Eligible hostile car/light vehicle destroyed | +5 PTS |
| Eligible hostile armored vehicle/APC/tank destroyed | +10 PTS |
| Eligible hostile aircraft/helicopter destroyed | +15 PTS |
| AO clear | +30 PTS |
| Side task completion | +10 PTS |
| Player death | -10 PTS |
| Player-caused Blue Force vehicle/equipment destruction | up to -25 PTS |

Blue Force destruction can also remove **10% of the currently active specialization XP**.

## 3. The 29-rank ladder

| PTS | Code | Rank |
| ---: | --- | --- |
| 0 | PVT | Private |
| 5 | PV2 | Private Second Class |
| 15 | PFC | Private First Class |
| 30 | SPC | Specialist |
| 50 | CPL | Corporal |
| 75 | SGT | Sergeant |
| 120 | SSG | Staff Sergeant |
| 180 | SFC | Sergeant First Class |
| 250 | MSG | Master Sergeant |
| 350 | 1SG | First Sergeant |
| 500 | SGM | Sergeant Major |
| 650 | CSM | Command Sergeant Major |
| 800 | SMA | Sergeant Major of the Army |
| 1,000 | WO1 | Warrant Officer 1 |
| 1,250 | CW2 | Chief Warrant Officer 2 |
| 1,550 | CW3 | Chief Warrant Officer 3 |
| 1,900 | CW4 | Chief Warrant Officer 4 |
| 2,300 | CW5 | Chief Warrant Officer 5 |
| 2,800 | 2LT | Second Lieutenant |
| 3,300 | 1LT | First Lieutenant |
| 3,900 | CPT | Captain |
| 4,600 | MAJ | Major |
| 5,400 | LTC | Lieutenant Colonel |
| 6,300 | COL | Colonel |
| 7,300 | BG | Brigadier General |
| 8,400 | MG | Major General |
| 9,600 | LTG | Lieutenant General |
| 11,000 | GEN | General |
| 12,500 | GA | General of the Army |

Promotion and demotion are calculated automatically from your current career points.

## 4. Specialization XP

Global rank and specialization development are separate. When positive specialization XP is awarded, the current lobby-assigned Operator Role receives the full award and every other specialization receives 1% of that award as cross-role XP. Cross-role XP does not recursively generate additional cross-role XP.

A normal player death keeps the standard career-point penalty and also removes **5% from every specialization that currently has XP**, calculated independently for each specialization and rounded upward.

Changing Operator Roles does not erase XP already earned in another role.

### Specialization equipment tiers

| Specialization | Active equipment tiers and XP thresholds |
| --- | --- |
| Recon JTAC / Recon | T1 0 / T2 50 / T3 125 |
| Combat Specialist | T1 0 / T2 100 / T3 275 / T4 550 |
| Mortar | T1 0 |
| Sniper | T1 0 / T2 200 / T3 800 / T4 1,200 |
| Anti-Armor / Air Defense | T1 0 / T2 150 / T3 375 / T4 675 |
| Heavy Gunner | T1 0 / T2 125 |
| Medic | T1 0 / T2 100 / T3 275 / T4 550 |
| Helicopter Pilot | T1 0 |

Tier thresholds are **specialization XP**, not military career points. The mission retains separate XP caps and saved career records. The mission's authored CUP inventories govern what each tier actually contains.

## 5. Operator Role capabilities

Role identity comes from the multiplayer lobby.

- **MEDIC** slots carry the configured ACE/ACM medical qualification and have four Arsenal tiers.
- **COMBAT_SPECIALIST** slots carry the mission's combat engineer / specialist access, including qualified EOD functions.
- **RECON** is authorized the NATO UAV terminal and Recon-exclusive Remington ACR EGLM grenade-launcher rifles.
- **MORTAR, SNIPER, ANTI_ARMOR, HEAVY_GUNNER and HELI_PILOT** receive their own role-specific equipment, not another role's restricted specialist gear.
- **HEAVY_GUNNER** primary machine guns/light support weapons use 100+ round ammunition; this restriction does not remove sidearm or SMG magazines.
- There is no playable **BATTLE_CAPTAIN**; historic XP data is preserved.

This keeps gameplay capability, equipment authorization and the selected multiplayer role aligned.

## 6. Ranked Arsenal

SENTINEL does not use an unrestricted Arsenal. Ranked Arsenal access is based on:

1. your **lobby-assigned Operator Role**;
2. your progress in that role;
3. the current specialization tier;
4. role-specific equipment and safety restrictions.

Equipment tiers are cumulative: reaching a higher tier keeps equipment already unlocked at lower tiers.

Role restrictions also apply to controlled equipment carried inside uniforms, vests and backpacks. An authorized container cannot be used to carry another role's restricted weapons, magazines, explosives, attachments, medical items, tools or other controlled equipment.

Ordinary battlefield loot outside the controlled SENTINEL Arsenal is not automatically role-locked.

The current BLUEFOR Arsenal is based on CUP Development with US Army OCP equipment as the mission standard; the legacy BWMod/BWA3 arsenal standard is retired. Terrain-aware camouflage affects AI detection according to equipped clothing and surroundings.

Medical and CBRN access, specialty equipment and role restrictions follow the current approved CUP role-tier inventories. Thermal optics are excluded by campaign policy.

## 7. Campaign continuity

Your career continues across SENTINEL deployments:

- military rank;
- career points;
- specialization XP for every role;
- Ranked Arsenal progression.

Each deployment has its own battlefield conditions, including AO progress, QRF activity, vehicles, aircraft, tickets, logistics, objectives and battlefield positions.

The active Operator Role always comes from the current multiplayer lobby slot.

## 8. What does not restart your career

Your operator career continues through:

- mission restarts;
- mission updates and new builds;
- changing deployment terrain;
- changing playable slot or character;
- beginning another SENTINEL deployment.

**New battlefield. Same operator. Same career.**

---

**SENTINEL** — NATO Special Forces Tactical Unit / NSFTU  
Continuing multi-terrain tactical co-op campaign for Arma 3.
