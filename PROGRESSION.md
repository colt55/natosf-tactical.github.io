# SENTINEL — Persistent Rank, XP, Specializations & Ranked Arsenal

Verified against **SENTINEL V2.04.65**.

SENTINEL is a continuing multi-terrain deployment campaign. A player's military rank, career points, selected specialization, specialization XP and Ranked Arsenal progression are stored as a **Global Career** tied to that player's Steam UID.

> **The deployment can change. The operator career continues.**

## 1. Global Career

SENTINEL preserves these progression records by Steam UID:

- Player rank record — UID, player name, hostile kills, deaths, career points and military rank.
- Selected specialization — the player's currently selected operational role.
- Specialization XP — independent persistent XP totals for every specialization.

The current specializations are:

- RECON
- DEMOLITIONS
- SNIPER
- ANTI-ARMOR
- HEAVY GUNNER
- MEDIC
- HELI PILOT

A player can change specialization only while physically at CENTCOM/base or beside the Command Vehicle. The tablet can be viewed elsewhere, but role changes remain location-gated.

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

Blue Force destruction also removes **10% of the player's currently selected specialization XP**. SENTINEL uses bounded attribution so ACE cook-off/secondary-destruction events do not create duplicate punishment transactions.

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

Global rank and specialization progression are separate records. Positive career gains also develop the specialization the player is actively operating.

A normal player death applies the standard career penalty and removes **5% of the currently selected specialization XP**, rounded upward.

Specialization XP is persistent and individually tracked for all seven roles. Switching roles does not erase XP already earned in another role.

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

## 5. Ranked Arsenal

The production Arsenal uses specialization-based authorization. SENTINEL combines:

1. the physical SENTINEL Arsenal Master/whitelist;
2. the player's selected specialization;
3. that specialization's persistent XP;
4. the active specialization tier;
5. role-specific equipment and safety restrictions.

Equipment tiers are cumulative: reaching a higher tier retains equipment already unlocked at lower tiers.

The standardized BWA3 apparel system exposes the approved Flecktarn, Multitarn and Tropentarn variants for appropriate non-pilot roles. Terrain-aware camouflage then affects AI detection performance based on the player's actual equipment and local environment.

CBRN-compatible Crye/ghillie uniforms and ACM filter access are available to non-pilot specialties. HELI PILOT remains excluded from the CBRN entitlement.

## 6. Deployment persistence split

SENTINEL V2.04.65 separates persistence into two layers:

### Global Career

Carries across every deployment:

- military rank;
- career points;
- selected specialization;
- specialization XP for every role.

### Deployment Battlefield

Remains isolated to the active deployment:

- AO and objective progress;
- QRF state;
- Blue Force and hostile persistent vehicles/aircraft;
- tickets;
- logistics and operational state;
- saved battlefield/player positions.

The Officer **CLEAR DATA** function deletes deployment battlefield state while preserving Global Career records. Once a clear is armed and confirmed, deployment-state saves remain blocked until server restart so the deleted battlefield cannot be recreated by a disconnect/autosave.

## 7. Continuity across deployments

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
