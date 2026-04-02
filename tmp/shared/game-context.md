# Game Project Master Context

> This file is the single source of truth for the project, referenced by all AI bots.
> The PD bot updates this file whenever an important decision is finalized.

## Basic Information
- **Game Title**: [TBD] (Candidates: Sprout Defense / Last Garden / Bloom War)
- **Genre**: Side-scrolling Defense
- **Platform**: Mobile
- **Target Session Length**: 2-3 minutes (per stage)
- **Development Tools/Engine**: [TBD]

## Design Pillars (3 Core Values)
1. Strategic Resource Trade-offs (Sap vs Seed allocation)
2. Unit Deck Building (choose from 20 types)
3. Cute yet Melancholic Aesthetic (Cozy Melancholy)

## Core Fantasy
> One sentence: The core experience the player should feel in this game
Become the last sprout and purify the corrupted world, recovering lost companions one by one.

## Elevator Pitch
> Two or three sentences: Explaining what this game is
A side-scrolling defense game where you play as "Sprout," the last sprout of the World Tree, reclaiming a corrupted continent.
Summon units with Seeds, use skills with Sap, and purify enemy bosses to reclaim them as allies.

## Reference Games
- Paladog: Side-scrolling defense core loop, Hero + Unit structure, dual resource system (Mana/Food)
- Clash of Clans: Witch unit (summons mini units with 1 HP) as reference

## World Setting

### Background — Edena and the Great Blight
- The continent **Edena**, where the World Tree **Arca** protected all life
- A **Blight** of unknown origin has consumed 90% of the continent
- Where surviving life has gathered: **"Last Garden"**, beneath Arca's last healthy branch
- Core tragedy: The enemies (the Blighted) were originally Edena's own companions

### Protagonist — Sprout
- A sprout spirit bloomed by Arca's last remaining power during the Great Blight
- A cute 15cm being with a small sprout on its head
- As Arca's last sprout, it is **irreplaceable** — Sprout's death = defeat
- The sprout wilts or blooms depending on emotions

### Allies — Guardians of the Garden
- Nature spirits & awakened animals faction
- 5 lineages (lineage = unlock tier per chapter):
  - Ch1 Sprout Lineage: Young spirits at the garden's border
  - Ch2 Forest Beast Lineage: Awakened animals from the forest outside the garden
  - Ch3 Ancient Tree Lineage: Ancient beings from deep within the old forest
  - Ch4 Swamp Lineage: Creatures adapted to the poison of the rotting lake
  - Ch5 Root Lineage: Primordial beings from deep within Arca's roots

### Enemies — The Blighted
- Originally Edena's native life forms, now infected by the Blight
- The Blight itself has no will, but story progression hints at something sentient at its core
- R40 Bosses = "Blighted versions" of unlockable units (purified ones join as allies)

### Tone & Art
- **"Cute yet Melancholic (Cozy Melancholy)"**
- Rounded 2-3 head-tall proportions, pastel-toned allies vs dark, murky enemies
- Green backgrounds on the ally side vs barren land on the enemy side

## Core Systems

### Dual Resource System
- **Sap**: Auto-generated, consumed for Sprout's skill usage
- **Seed**: Consumed for unit summoning

### Core Loop
```
Seed/Sap generation → Summon units (Seed) or Use skills (Sap) → Auto-combat → Wave clear → Rewards
```
- Victory = Destroy enemy base
- Defeat = Sprout's death
- Star rating system (3 Stars = no-damage clear)

### Unit System
- 3 Roles: Tank / DPS / Support
- No elemental system — differentiated by **attack type**
- **Every unit has a unique role (no role overlap allowed)**
- Deployment deck slots (initial 4, max 6)
- Unit leveling: In-game enemy kills → earn EXP + Gold, level up in out-of-game UI (meet EXP requirement + spend Gold), max Lv.20, simple stat increases
- R40 chapter boss purification unlocks units

### Implementation Constraints
- No units that cling to enemies (not implementable)
- No ground-placement units (not implementable)
- Melee attacks OK
- Ranged projectiles OK
- Area-of-effect OK
- Effect-type (triggers at enemy position) OK

### 20 Unit Roster

#### Ch1 — Sprout Lineage (Around the Last Garden)
| Unlock | Name | Role | Type | Description |
|--------|------|------|------|-------------|
| R1 | Thorn | DPS | Basic Melee | Stabs with thorns. Cheap and fast, low HP |
| R10 | Acorn | Tank | HP Tank | Endures with a hard shell |
| R20 | Dandy (Dandelion) | DPS | Ranged | Ranged damage by blowing seeds |
| R40 | Snail | Support | Slow | Slows enemies with slime projectiles [Purified] |

#### Ch2 — Forest Beast Lineage (Forest Outside the Garden)
| Unlock | Name | Role | Type | Description |
|--------|------|------|------|-------------|
| R1 | Hedgie (Hedgehog) | DPS | AoE | Rolls as a spike ball, hitting nearby enemies |
| R10 | Bee | Support | Healer | Heals allies by applying honey |
| R20 | Bear | Tank | Taunt | Draws aggro with a roar |
| R40 | Woody (Woodpecker) | DPS | Rapid Hits | High-speed multi-hit. Single-target DPS for boss fights [Purified] |

#### Ch3 — Ancient Tree Lineage (Deep Forest)
| Unlock | Name | Role | Type | Description |
|--------|------|------|------|-------------|
| R1 | Scorpion | DPS | DoT | Damage over time with venomous stinger |
| R10 | Oakguard (Tree Golem) | Tank | Knockback | Pushes enemies back with giant arms |
| R20 | Bloom (Flower Fairy) | Support | Buffer | Buffs allies with pollen |
| R40 | Shroom (Mushroom) | Support | Summoner | Summons mini mushrooms (1 HP) with spores [Purified] |

#### Ch4 — Swamp Lineage (Rotting Lake)
| Unlock | Name | Role | Type | Description |
|--------|------|------|------|-------------|
| R1 | Heron | DPS | Piercing | Linear piercing with its long beak |
| R10 | Poison Frog | Support | Debuffer | Reduces enemy stats by spraying poison |
| R20 | Turtle | Tank | Shield | Grants ally shields with its shell |
| R40 | Venus (Venus Flytrap) | DPS | %HP Damage | Bites for max HP% damage [Purified] |

#### Ch5 — Root Lineage (Arca's Roots)
| Unlock | Name | Role | Type | Description |
|--------|------|------|------|-------------|
| R1 | Frog | DPS | Isolate + Sustained | Grabs with tongue and chews; spits out if not killed |
| R10 | Roottrap | Support | Stun | Roots burst up to bind enemies |
| R20 | Crystal | Tank | Reflect | Reflects damage back to attackers |
| R40 | Hawk | DPS | Execute | Deals bonus damage when enemy HP is below a threshold [Purified] |

Role distribution: DPS 9 / Tank 5 / Support 6 = 20 types

### R40 Boss Purification Links
| Ch | Blighted Boss | → Purified Unit | Twist |
|----|---------------|-----------------|-------|
| 1 | Toxic Moss (dissolves on contact) | → Snail (Slow) | Dissolve → Slow |
| 2 | Frenzied Raptor (mad pecking) | → Woodpecker (Rapid Hits) | Frenzy → Control |
| 3 | Toxic Mushroom (zombification via toxic spores) | → Mushroom (Ally Summon) | Enemy summon → Ally summon |
| 4 | Giant Carnivorous Plant (indiscriminate devouring) | → Venus Flytrap (%HP Damage) | Devour → Shred |
| 5 | Blighted Raptor (indiscriminate assault) | → Hawk (Execute) | Indiscriminate → Precise finishing |

### Unit Placement Principles
- R1 first unit must be DPS (not Tank)
- No healer given in Chapter 1
- R40 boss purification unit = fills the role that chapter was lacking
- Unit name/appearance should immediately convey its function
- Must comply with implementation constraints (no clinging to enemies, no ground placement)

### Hero (Sprout) System
- Direct control: Position movement (front/back) + 3 equipped skills
- Front: Aura buff to units, risk of being stunned
- Back: Safe, outside aura range
- Skills consume Sap
- Equip 3 from a total pool of 9-12 skills

### Stage Structure
- **5 Chapters x 40 Rounds = 200 Rounds**
- Every 10 rounds: Mid-boss
- Every 40 rounds: Chapter final boss
- Boss fights: Pattern-based (skill timing is key)
- Boss kill → Purification cinematic → Ally unit unlock
- R40 Boss = "Blighted version" of the unlocked unit
- Unit unlocks: R1 (1st), R10 (2nd), R20 (3rd), R40 (4th = purified unit)
- Chapter-specific environmental effects
- Story progression: Garden → Forest → Deep Forest → Swamp → Arca's Roots (source of Blight)

### Endless Mode — "Memories of Arca"
- Entry: Unlocked after clearing Chapter 2
- Setting: Relive past threats within Arca's millennia of memories
- Every 5 waves: "Legacy of the Former Guardians" roguelite buff — pick 1 of 3
- Enemy stats scale infinitely at +5-8% per wave
- Sharp difficulty spike past 30 minutes → naturally encourages session end

## Current Stage
- [x] Ideation
- [x] Core loop finalized
- [x] World setting pillars finalized
- [x] 20 unit roster finalized
- [x] Chapter-wise unit placement finalized
- [ ] Prototype development started
- [ ] Prototype validation
