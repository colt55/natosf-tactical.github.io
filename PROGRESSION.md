# SENTINEL — Persistent Rank, XP, Operator Roles & Ranked Arsenal

Verified against **SENTINEL V2.04.69**.

SENTINEL is a continuing multi-terrain deployment campaign. A player's military rank, career points, specialization XP and Ranked Arsenal progression are stored as a **Global Career** tied to that player's Steam UID. The active **Operator Role** for a session is assigned by the multiplayer lobby slot.

> **The deployment can change. The operator career continues. The lobby slot assigns the active role.**

## 1. Global Career and Operator Role

SENTINEL preserves these progression records by Steam UID:

- Player rank record — UID, player name, hostile kills, deaths, career points and military rank.
- Specialization XP — independent persistent XP totals for every specialization.
- Ranked Arsenal progression derived from each specialization's persistent XP.

The current Operator Roles are:

- RECON
- DEMOLITIONS
- SNIPER
- ANTI-ARMOR
- HEAVY GUNNER
- MEDIC
- HELI PILOT

The **multiplayer lobby slot is the sole authority for the active Operator Role**. A player changes specialization by returning to the multiplayer lobby and selecting a different role slot. The CENTCOM Tablet **OPERATOR ROLE** page is view/status only and cannot change the role.

Changing lobby slots does not erase specialization XP already earned in another role.

## 2. Career points and rank

Career points (`PTS`) determine the player's military rank.

The standard calculation remains based on hostile kills, persistent campaign rewards and penalties, with a floor of zero.

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

Blue Force destruction also removes **10% of the player's currently active specialization XP**. SENTINEL uses bounded attribution so ACE cook-off/secondary-destruction events do not create duplicate punishment transactions.

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

Promotion and demotion are calculated automatically from the saved UID record.

## 4. Specialization XP

Global rank and specialization progression are separate records. Positive career gains also develop the specialization represented by the player's current lobby-assigned Operator Role.

A normal player death applies the standard career penalty and removes **5% of the currently active specialization XP**, rounded upward.

Specialization XP is persistent and individually tracked for all seven roles. Changing lobby slots does not erase XP already earned in another role.

### Specialization equipment tiers

| Specialization | Tier thresholds | Mastery / persistent cap |
| --- | --- | ---: |
| RECON | T1 0 / T2 50 / T3 125 / T4 250 / T5 450 | 495 XP |
| DEMOLITIONS | T1 0 / T2 100 / T3 275 / T4 550 | 605 XP |
| SNIPER | T1 0 / T2 200 / T3 450 / T4 800 / T5 1,200 | 1,320 XP |
| ANTI-ARMOR | T1 0 / T2 150 / T3 375 / T4 675 | 743 XP |
| HEAVY GUNNER | T1 0 / T2 125 / T3 350 | 385 XP |
| MEDIC | T1 0 | 605 XP persistent-stat cap |
| HELI PILOT | T1 0 | 605 XP persistent-stat cap |

MEDIC and HELI PILOT intentionally use one equipment tier while retaining persistent specialization XP as a career statistic.

## 5. Operator Role capabilities

Role identity now comes from the multiplayer lobby rather than a Tablet selection.

- **MEDIC** slots carry the configured ACE/ACM medical qualification.
- **DEMOLITIONS** slots carry Advanced Engineer and EOD qualification.
- **RECON, SNIPER, ANTI-ARMOR, HEAVY GUNNER and HELI PILOT** do not inherit MEDIC or DEMOLITIONS ACE role qualifications simply by changing equipment.
- The CENTCOM Tablet **OPERATOR ROLE** page reports the current role and progression but does not provide a role-change control.

This keeps gameplay capability, equipment authorization and the player's selected multiplayer role aligned to the same authoritative slot identity.

## 6. Ranked Arsenal and entitlement enforcement

The production Arsenal uses specialization-based authorization. SENTINEL combines:

1. the physical SENTINEL Arsenal Master/whitelist;
2. the player's **lobby-assigned Operator Role**;
3. that role's persistent specialization XP;
4. the active specialization tier;
5. role-specific equipment and safety restrictions.

Equipment tiers are cumulative: reaching a higher tier retains equipment already unlocked at lower tiers.

Controlled SENTINEL equipment is also checked after inventory transfers. Entitlement enforcement examines the complete carried loadout, including controlled items stored inside uniforms, vests and backpacks. An authorized container cannot be used to carry another role's restricted weapons, magazines, explosives, attachments, medical items, tools or other controlled equipment.

This restriction applies to equipment that belongs to the controlled SENTINEL Arsenal Master. Ordinary battlefield loot outside that controlled equipment set is not automatically specialization-locked.

The standardized BWA3 apparel system exposes the approved Flecktarn, Multitarn and Tropentarn variants for appropriate non-pilot roles. Terrain-aware camouflage then affects AI detection performance based on the player's actual equipment and local environment.

CBRN-compatible Crye/ghillie uniforms and ACM filter access are available to non-pilot specialties. HELI PILOT remains excluded from the CBRN entitlement.

## 7. Deployment persistence split

SENTINEL V2.04.69 separates persistence into two layers:

### Global Career

Carries across every deployment:

- military rank;
- career points;
- specialization XP for every role;
- resulting Ranked Arsenal progression.

The active Operator Role is supplied by the current multiplayer lobby slot rather than selected from the persistent battlefield state.

### Deployment Battlefield

Remains isolated to the active deployment:

- AO and objective progress;
- QRF state;
- Blue Force and hostile persistent vehicles/aircraft;
- tickets;
- logistics and operational state;
- saved battlefield/player positions.

The Officer **CLEAR DATA** function deletes deployment battlefield state while preserving Global Career records. Once a clear is armed and confirmed, deployment-state saves remain blocked until server restart so the deleted battlefield cannot be recreated by a disconnect/autosave.

## 8. Continuity across deployments

The following do **not** reset the operator career:

- mission restarts;
- mission updates and new builds;
- changing deployment terrain;
- changing playable slot or character;
- Officer deployment-data reset;
- beginning another SENTINEL deployment.

The battlefield can change completely. The operator does not start over.

---

**SENTINEL** — NATO Special Forces Tactical Unit / NSFTU  
Persistent multi-terrain tactical co-op campaign for Arma 3.
