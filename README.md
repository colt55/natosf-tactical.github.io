# NSFTU — SENTINEL

Official public information hub for **SENTINEL**, the persistent multi-terrain tactical co-op / MilSim campaign of the **NATO Special Forces Tactical Unit (NSFTU)** for Arma 3.

## Campaign Standard

- **Mission:** SENTINEL
- **Build:** V2.04.69
- **Deployment Model:** Multi-terrain
- **BLUEFOR Standard:** BWMod / BWA3
- **OPFOR Standard:** RHS Armed Forces of the Russian Federation
- **Objective Compatibility:** Arma 3 + official DLC terrain objects or CUP Terrain Core objects
- **Gameplay:** Persistent tactical co-op / MilSim

SENTINEL uses one common campaign framework across deployments. Terrain, base placement, Areas of Operation and battlefield state can change without rebuilding the core campaign or resetting operator progression.

## Connect

- **Server:** `85.190.160.165:10600`
- **Server Browser:** `Operation Sentinel Server [ACE/ACRE/ACM]`
- **Discord:** https://discord.gg/6XrZ6t52E
- **TeamSpeak / ACRE2:** `ts107.nitrado.net:10450`
- **TeamSpeak Password:** `FALCON7`

## Core Required Mods

The permanent SENTINEL core client stack is:

- CBA_A3
- ACE3
- Advanced Combat Medicine (ACM)
- ACRE2
- RHS Armed Forces of the Russian Federation (RHSAFRF)
- BWMod / BWA3

The terrain package varies by deployment and is supplied through the active Workshop collection.

**Steam Workshop Collection:**  
https://steamcommunity.com/sharedfiles/filedetails/?id=3495986928

## Deployment Architecture

SENTINEL separates persistence into two layers:

- **Global Career:** military rank, career points and independent specialization XP for every role follow the operator across every SENTINEL deployment.
- **Deployment Battlefield:** AO progress, QRF state, vehicles, aircraft, tickets, logistics, objectives and battlefield positions remain isolated to the current deployment.

The active **Operator Role** is assigned by the player's multiplayer lobby slot for the current session. Changing slots changes the active role without deleting XP already earned in any specialization.

Officer campaign reset tools clear the deployment battlefield without deleting the Global Career database.

## Campaign Capabilities

SENTINEL includes persistent player progression and Ranked Arsenal authorization; lobby-assigned Operator Roles; dynamic Areas of Operation and terrain-object objectives; scalable AI/QRF response; the CENTCOM Tablet; Officer command tools; TALCS tactical aviation support; persistent Blue Force assets; logistics, towing and recovery; tactical airlift; ACE/ACM medical gameplay; ACRE2 tactical communications; and terrain-aware camouflage behavior.

### QRF Wave Director

QRF pressure scales with real player count. Hidden reinforcement opportunities dispatch one maximum-skill ground vehicle or attack helicopter at a time, gated by AO progress, randomized spacing and a live-platform performance cap. The hidden plan and surviving QRF state persist through server restart.

### Standard Blue Force Capability

- **EAGLE 1–4** — BWMod tactical vehicles
- **OVERLORD** — Command Vehicle / support platform
- **MULTI A4 1–2** — persistent multifunction logistics vehicles with towing support
- **LIFTER 1–2** — heavy and light tactical rotary-wing lift
- Marine assets are available through SENTINEL Logistics when applicable

### Operator Roles — Lobby Assigned

RECON · DEMOLITIONS · SNIPER · ANTI-ARMOR · HEAVY GUNNER · MEDIC · HELI PILOT

The multiplayer lobby slot is the sole authority for the active role. The CENTCOM Tablet **OPERATOR ROLE** page is status/progression only; it does not change specialization.

Role-qualified ACE/ACM capabilities follow the slot: MEDIC slots carry the medical qualification, while DEMOLITIONS slots carry Advanced Engineer and EOD qualification. Other combat-role slots do not inherit those qualifications.

## Persistent Rank, XP & Ranked Arsenal

SENTINEL maintains a persistent career record for each operator. The record includes career points, military rank, persistent XP for every specialization and the resulting Ranked Arsenal equipment tier.

Ranked Arsenal authorization is resolved from the current lobby-assigned Operator Role plus that role's persistent XP/tier. Controlled SENTINEL equipment is recursively entitlement-checked, including controlled items stored inside carried uniforms, vests and backpacks; an authorized container cannot be used to bypass another role's equipment restrictions.

That Global Career carries forward across SENTINEL deployments. A new battlefield is not a new operator career.

**Full system documentation:** [Persistent Rank, XP, Operator Roles & Ranked Arsenal](PROGRESSION.md)

## NSFTU Links

- **Website:** https://colt55.github.io/natosf-tactical.github.io/
- **Discord:** https://discord.gg/6XrZ6t52E
- **Steam Group:** https://steamcommunity.com/groups/natosf-tactical
- **Steam Workshop Collection:** https://steamcommunity.com/sharedfiles/filedetails/?id=3495986928
- **Arma 3 Unit:** https://units.arma3.com/unit/nsft
- **Contact:** natosf.command@protonmail.com

SENTINEL welcomes new and experienced Arma 3 players interested in serious cooperative tactical gameplay, persistent progression, infantry, reconnaissance, demolitions, anti-armor, heavy weapons, medical operations, aviation, logistics and recovery.
