# SENTINEL — Persistent Rank, XP, Specializations & Ranked Arsenal

Verified against **SENTINEL V2.04.40 Stubbhult**.

SENTINEL is built as a continuing campaign rather than a collection of disposable missions. A player's combat record, rank, selected specialization, specialization XP and Ranked Arsenal progression are server-authoritative persistent records tied to that player's **Steam UID**.

The important design rule is simple:

> **The map, faction, player slot and character object can change. The player's UID progression record is the identity that continues.**

## 1. What SENTINEL saves for every player

The campaign persistence payload stores three progression layers by Steam UID:

- **Player Rank Record** — UID, player name, hostile kills, deaths, career points, current rank and persistent bonus/reward points.
- **Selected Specialization** — the player's currently selected operational role.
- **Specialization XP** — independent persistent XP totals for each specialization.

The six current specializations are:

- RECON
- DEMOLITIONS
- SNIPER
- ANTI-ARMOR
- HEAVY GUNNER
- MEDIC

A player can change specialization only while physically at CENTCOM/base or beside a deployed Command Vehicle. The tablet can be viewed elsewhere, but role changes are server-authoritative and location-gated.

## 2. Global career points and rank

Global career points (`PTS`) determine the player's military rank.

The current calculation is:

`PTS = max(0, hostile infantry kills + persistent bonus/reward points - (deaths × 10))`

### Current point sources

| Event | Award |
| --- | ---: |
| Countable hostile infantry kill | +1 kill / +1 PTS |
| Mission static weapon destroyed | +3 PTS |
| Mission car/light vehicle destroyed | +5 PTS |
| Mission armored vehicle/APC/tank destroyed | +10 PTS |
| Mission aircraft/helicopter destroyed | +15 PTS |
| Other eligible mission vehicle destroyed | +5 PTS |
| AO clear | +30 PTS |
| Side task completion | +10 PTS |
| Player death | -10 PTS |

Vehicle awards are limited to eligible SENTINEL mission vehicles/targets and use server-side kill attribution, including bounded ACE cook-off attribution so a valid player hit is not lost when ammunition cook-off finishes the vehicle later.

AO-clear and side-task completion rewards are shared campaign rewards. Connected human players inside the protected **1,000 m BASE reward-exclusion zone** do not receive those shared completion points. This prevents players sitting at base from accumulating objective progression.

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

Promotion and demotion are calculated server-side from the saved UID record. The CENTCOM Tablet rank page displays the current rank, KIA, deaths, PTS, next rank requirement, selected specialization, specialization XP and active specialization equipment tier.

## 4. Specialization XP

Global rank and specialization progression are related, but they are not the same number.

Whenever a player earns a **positive global point gain**, that gain is also credited to the specialization currently selected for that player. This means a player develops the role they are actually operating while continuing to build one overall military rank record.

A death has two progression effects:

1. Global career points receive the normal **-10 PTS** death penalty.
2. The currently selected specialization loses **5% of its existing specialization XP**, rounded upward.

Specialization XP is persistent and individually tracked for all six roles. Switching roles does not erase the XP already earned in another role.

### Specialization equipment tiers

| Specialization | Tier thresholds | Mastery cap |
| --- | --- | ---: |
| RECON | T1 0 / T2 50 / T3 125 / T4 250 / T5 450 | 495 XP |
| DEMOLITIONS | T1 0 / T2 100 / T3 275 / T4 550 | 605 XP |
| SNIPER | T1 0 / T2 200 / T3 450 / T4 800 / T5 1,200 | 1,320 XP |
| ANTI-ARMOR | T1 0 / T2 150 / T3 375 / T4 675 | 743 XP |
| HEAVY GUNNER | T1 0 / T2 125 / T3 350 | 385 XP |
| MEDIC | T1 0 | 605 XP persistent-stat cap |

The mastery cap is normally 110% of the highest equipment-unlock threshold. MEDIC intentionally has one equipment tier while retaining persistent specialization XP as a career statistic.

## 5. How the Ranked Arsenal uses progression

The production Arsenal uses **specialization-based authorization**.

The server combines:

1. the physical SENTINEL Arsenal Master/whitelist;
2. the player's selected specialization;
3. that specialization's persistent XP;
4. the active specialization tier;
5. role-specific safety restrictions.

Equipment tiers are cumulative: reaching a higher tier retains the equipment from lower tiers.

Examples of role-specific enforcement include dedicated sniper equipment, demolitions equipment, anti-armor launchers and ammunition, medic equipment, and a Heavy Gunner-only safety gate for high-capacity machine-gun magazines.

The vanilla `ToolKit` is intentionally available to every active specialization/tier.

SENTINEL also enforces entitlement when relevant Arsenal-master equipment is taken or restored through controlled loadout systems. Battlefield equipment that is outside the controlled SENTINEL Arsenal Master is not automatically treated as specialization-locked loot.

The old eight-tier rank Arsenal resolver remains in the mission as a fallback, but **the active production system is the specialization-role framework described above**.

## 6. How progression is saved

Progression is server-authoritative and written through SENTINEL's campaign persistence system.

The campaign payload includes:

- `playerRanks`
- `playerRoles`
- `playerSpecializations`

SENTINEL writes the payload to Arma's server-side `profileNamespace` under both:

- a terrain-specific SENTINEL campaign key; and
- a legacy/portable SENTINEL campaign alias.

Rank/progression transactions queue a bounded autosave. The current rank autosave delay is **60 seconds**. Normal campaign saves also include the same progression records.

Because records are keyed by **Steam UID**, changing player slot, respawning, changing faction/template, or rebuilding the playable character does not create a new rank identity.

## 7. Terrain changes and deployments

Player progression is treated differently from physical campaign state.

When SENTINEL moved to Stubbhult, the migration path was deliberately designed to import the portable UID progression slice—rank records, selected roles and specialization XP—without importing old terrain positions, AO geometry, vehicles or objectives from the previous terrain.

That is the intended deployment model:

> **Carry the operator record forward; rebuild terrain-specific battlefield state for the new deployment.**

Future terrain deployments should preserve the same portable progression slice when a new world-specific campaign key is created.

## 8. Moving SENTINEL to another server

The Steam UID makes the record player-portable, but the saved database itself lives in the **Arma server profile/profileNamespace**.

Therefore:

- restarting the same server/mission preserves progression;
- updating the mission build preserves progression;
- changing playable slots or faction does not affect the UID record;
- terrain migration can preserve progression through the portable progression migration path;
- moving to entirely new server hardware/profile requires the SENTINEL server profile/profileNamespace data to be migrated to the new server.

A fresh server profile with no copied persistence database cannot know the old ranks automatically. The authoritative campaign database must move with the server.

## 9. What a player's record means

A SENTINEL operator's progression is not just a scoreboard.

The persistent record determines and records:

- career military rank;
- combat kills and deaths;
- objective/mission reward points;
- current specialization;
- XP accumulated in every specialization;
- specialization equipment tier;
- Ranked Arsenal authorization.

That continuity is intended to survive deployments. A new terrain or faction is a new operational environment—not a new operator career.

---

**SENTINEL** — NATO Special Forces Tactical Unit / NSFTU  
Persistent tactical co-op campaign for Arma 3.
