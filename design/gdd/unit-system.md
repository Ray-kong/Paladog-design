# Unit System — 20 Types Final Confirmation (v1.0)

> **Design Principles:**
> - No elemental attributes, distinguished only by attack type
> - No overlapping roles — every unit has a unique reason to be used
> - Name/appearance should immediately convey what the unit does
> - R1 is always a dealer, healer is not given in Ch1

> **Implementation Constraints:**
> - ❌ Units that attach to enemies
> - ❌ Units placed on the ground
> - ✅ Melee strike / Ranged projectile / Area effect / Effect-type (triggers at enemy position)

## Roles — All 20 Types

### Dealers (8 Types)
| # | Type | Description |
|---|------|-------------|
| 1 | Basic Melee | Cheap and fast, low HP |
| 2 | Ranged | Safe damage from the back |
| 3 | AoE | Clears mob swarms |
| 4 | Rapid Strike | Single-target DPS, for bosses |
| 5 | %Damage | Dedicated to high-HP enemies |
| 6 | Piercing | Penetrates multiple enemies in a straight line |
| 7 | DoT | Poison sting, sustained damage |
| 8 | Isolation+Sustained DPS | Grabs with tongue and chews, spits out if not killed |
| 9 | Execute | Extra damage when enemy HP falls below a certain % |

### Tanks (5 Types)
| # | Type | Description |
|---|------|-------------|
| 10 | HP Tank | Survives without dying |
| 11 | Taunt Tank | Draws aggro |
| 12 | Knockback | Pushes the front line |
| 13 | Reflect | Reflects damage taken |
| 14 | Shield | Grants shield to allies |

### Supporters (6 Types)
| # | Type | Description |
|---|------|-------------|
| 15 | Healer | Restores allies |
| 16 | Buffer | Strengthens allies |
| 17 | Slow | Slows enemies |
| 18 | Summoner | Continuously summons mini units with 1 HP |
| 19 | Debuffer | Reduces enemy ATK/DEF |
| 20 | Stun | Hard CC, completely stops actions |

**Final Distribution: Dealers 9 / Tanks 5 / Supporters 6 = 20 Types**

---

## Unit 20 Types Detail — Final Confirmation

### Ch1 — Sprout Series (Around the Last Garden)

| Unlock | Unit Name | Role | Type | Cost (Seeds) | Cooldown | Implementation |
|--------|-----------|------|------|-------------|----------|----------------|
| R1 | **Thorn** | Dealer | Basic Melee | 30 | 3s | Melee strike |
| R10 | **Acorn** | Tank | HP Tank | 80 | 8s | Area effect (damage absorption) |
| R20 | **Dandy** | Dealer | Ranged | 45 | 5s | Ranged projectile |
| R40🔓 | **Snail** | Supporter | Slow | 55 | 8s | Ranged projectile (slime) |

**R40 Purification Boss**: Toxic Moss → Snail. "Dissolve → Slow"
**Ch1 Gap Fill**: Supporter 0 → Slow Supporter acquired

---

### Ch2 — Forest Beast Series (Forest Outside the Garden)

| Unlock | Unit Name | Role | Type | Cost (Seeds) | Cooldown | Implementation |
|--------|-----------|------|------|-------------|----------|----------------|
| R1 | **Hedgie** | Dealer | AoE | 55 | 6s | Area effect (spike ball) |
| R10 | **Bee** | Supporter | Healer | 60 | 10s | Area effect (honey heal) |
| R20 | **Bear** | Tank | Taunt Tank | 100 | 10s | Area effect (roar) |
| R40🔓 | **Woody** | Dealer | Rapid Strike | 65 | 7s | Melee strike (high-speed rapid hits) |

**R40 Purification Boss**: Frenzied Raptor → Woodpecker. "Rampage → Control"
**Ch2 Gap Fill**: Lacking single-target boss DPS → Rapid Strike boss killer acquired

---

### Ch3 — Ancient Tree Series (Deep Forest)

| Unlock | Unit Name | Role | Type | Cost (Seeds) | Cooldown | Implementation |
|--------|-----------|------|------|-------------|----------|----------------|
| R1 | **Scorpion** | Dealer | DoT | 50 | 6s | Melee strike (poison sting) |
| R10 | **Oakguard** | Tank | Knockback | 110 | 11s | Melee strike (push) |
| R20 | **Bloom** | Supporter | Buffer | 65 | 10s | Area effect (pollen) |
| R40🔓 | **Shroom** | Supporter | Summoner | 70 | 9s | Area effect (spores → mini units) |

**R40 Purification Boss**: Toxic Mushroom → Shroom. "Enemy summon → Ally summon"
**Ch3 Gap Fill**: Lacking numbers/front line support → Summoner mini units provide numbers

**Shroom Balancing:**
- Mini Mushroom: 1 HP, weak melee attack
- Summon interval: 1 unit every 2~3 seconds
- Simultaneous cap: 4~5 units
- Wiped by AoE but re-summoned = "tenacious vitality"

---

### Ch4 — Swamp Series (Rotten Lake)

| Unlock | Unit Name | Role | Type | Cost (Seeds) | Cooldown | Implementation |
|--------|-----------|------|------|-------------|----------|----------------|
| R1 | **Heron** | Dealer | Piercing | 60 | 7s | Melee strike (beak stab, straight-line piercing) |
| R10 | **Poison Frog** | Supporter | Debuffer | 55 | 9s | Ranged projectile (poison) |
| R20 | **Turtle** | Tank | Shield | 95 | 10s | Area effect (shield grant) |
| R40🔓 | **Venus** | Dealer | %Damage | 80 | 9s | Melee strike (bite) |

**R40 Purification Boss**: Giant Carnivorous Plant → Venus. "Devour → Shred"
**Ch4 Gap Fill**: Cannot handle ultra-high HP bosses → Compensated with %Damage

---

### Ch5 — Root Series (Roots of Arca)

| Unlock | Unit Name | Role | Type | Cost (Seeds) | Cooldown | Implementation |
|--------|-----------|------|------|-------------|----------|----------------|
| R1 | **Frog** | Dealer | Isolation+Sustained DPS | 75 | 10s | Melee (tongue grab → chew → spit) |
| R10 | **Roottrap** | Supporter | Stun | 75 | 15s | Effect-type (triggers at enemy position) |
| R20 | **Crystal** | Tank | Reflect | 100 | 11s | Area effect (damage reflect) |
| R40🔓 | **Hawk** | Dealer | Execute | 85 | 8s | Ranged (diving strike) |

**R40 Purification Boss**: Corroded Raptor → Hawk. "Indiscriminate → Precise finishing"
**Ch5 Gap Fill**: Lacking decisive finishing power → Execute dealer acquired

**Frog Mechanic Details:**
```
[Tongue launch] → [Isolate 1 enemy] → [Chew = sustained DPS] → [Death or timeout (3~5s) → Spit out]
```
- Isolated enemy cannot deal/take damage from other units
- Frog also cannot perform other actions while chewing (self-isolated state)
- Tactic: Remove 1 dangerous enemy from the front line

**Hawk Mechanic Details:**
```
Basic attack: Ranged single-target hit (normal damage)
Execute effect: 3x damage when enemy HP is below 30%
```
- Forms a "shred ↔ finish" pair with Venus (%Damage)
- Boss fight: Shred HP with Venus → Finish with Hawk

---

## Overall Role Distribution

| Role | Count | Units |
|------|-------|-------|
| **Dealers (9)** | Thorn, Dandy, Hedgie, Woody, Scorpion, Heron, Venus, Frog, Hawk |
| **Tanks (5)** | Acorn, Bear, Oakguard, Turtle, Crystal |
| **Supporters (6)** | Snail, Bee, Bloom, Shroom, Poison Frog, Roottrap |

### Cumulative Unit Pool
| Point | Total | Dealers | Tanks | Supporters |
|-------|-------|---------|-------|------------|
| Ch1 Complete | 4 | 2 | 1 | 1 |
| Ch2 Complete | 8 | 4 | 2 | 2 |
| Ch3 Complete | 12 | 5 | 3 | 4 |
| Ch4 Complete | 16 | 7 | 4 | 5 |
| Ch5 Complete | 20 | 9 | 5 | 6 |

---

## Deployment Deck
- Select from 20 types with slot limit (initial 4, max 6)
- No duplicate units allowed in deck (same unit in deck ❌)
- Summoning multiple copies of the same unit is possible in-game

## Production Resource
- **Seed**: Unit summoning only
- Max simultaneous units: 15~20 (considering performance)
- Summoner (Shroom) mini units have a separate count (cap 4~5)

## Unit Level-Up System (Meta, Permanent)

### Basic Structure
- **EXP Acquisition**: Earn EXP from killing enemies in-game (only units in the deck)
- **Gold Acquisition**: Earn small amounts of gold from killing enemies in-game (+2~5 gold/kill)
- **Level-Up Location**: Separate UI outside of gameplay
- **Level-Up Condition**: EXP met + Gold spent
- **Level-Up Effect**: Simple stat increase (ATK/HP, etc.)
- **Max Level**: 20

### Stat Increase per Level (Cumulative vs Lv.1)
| Phase | Level | Per Level | Phase Cumulative | Total Cumulative |
|-------|-------|-----------|-----------------|-----------------|
| Early | 1→5 | +3% | +12% | +12% |
| Mid | 6→10 | +4% | +20% | +32% |
| Late | 11→15 | +5% | +25% | +57% |
| Master | 16→20 | +8~9% | +43% | +100% |

### Gold Cost Curve
**Design Intent**: Late-level costs increase sharply, making it more efficient to raise new units to low levels than to push existing units to high levels. This provides the economic incentive for adopting new units.

| Level | Cost | Cumulative | | Level | Cost | Cumulative |
|-------|------|------------|-|-------|------|------------|
| 2 | 30 | 30 | | 12 | 550 | 1,640 |
| 3 | 40 | 70 | | 13 | 750 | 2,390 |
| 4 | 50 | 120 | | 14 | 1,000 | 3,390 |
| 5 | 70 | 190 | | 15 | 1,300 | 4,690 |
| 6 | 100 | 290 | | 16 | 1,700 | 6,390 |
| 7 | 130 | 420 | | 17 | 2,200 | 8,590 |
| 8 | 170 | 590 | | 18 | 2,800 | 11,390 |
| 9 | 220 | 810 | | 19 | 3,500 | 14,890 |
| 10 | 280 | 1,090 | | 20 | 4,500 | 19,390 |

**Key Comparison Example:**
- Thorn (Ch1) Lv.12→13 cost: **750 Gold**
- Scorpion (Ch3) Lv.1→5 cost: **190 Gold** + Scorpion has higher base stats
- → Investing in new units is economically rational

### New Unit Adoption Balance
- No artificial systems like catch-up EXP ❌
- **Later chapter units have higher base stats, naturally balancing through design**
- Cost curve provides economic incentive → investing in new units is more efficient

## Unit Unlock Path (Final)

| Chapter | R1 | R10 | R20 | R40 (Purification) |
|---------|-----|------|------|---------------------|
| Ch1 | Thorn (Dealer/Melee) | Acorn (Tank/HP) | Dandy (Dealer/Ranged) | Snail (Supporter/Slow) |
| Ch2 | Hedgie (Dealer/AoE) | Bee (Supporter/Heal) | Bear (Tank/Taunt) | Woody (Dealer/Rapid Strike) |
| Ch3 | Scorpion (Dealer/DoT) | Oakguard (Tank/Knockback) | Bloom (Supporter/Buffer) | Shroom (Supporter/Summon) |
| Ch4 | Heron (Dealer/Piercing) | Poison Frog (Supporter/Debuff) | Turtle (Tank/Shield) | Venus (Dealer/%Damage) |
| Ch5 | Frog (Dealer/Isolation) | Roottrap (Supporter/Stun) | Crystal (Tank/Reflect) | Hawk (Dealer/Execute) |

## R40 Boss Purification Connections (Final)

| Ch | Corrupted Boss | → Purified Unit | Reversal |
|----|----------------|-----------------|----------|
| 1 | Toxic Moss (dissolves on contact) | → Snail (Slow) | Dissolve → Slow |
| 2 | Frenzied Raptor (mad pecking) | → Woodpecker (Rapid Strike) | Rampage → Control |
| 3 | Toxic Mushroom (poison spore zombification) | → Shroom (Ally Summon) | Enemy summon → Ally summon |
| 4 | Giant Carnivorous Plant (indiscriminate feeding) | → Venus (%Damage) | Devour → Shred |
| 5 | Corroded Raptor (indiscriminate raids) | → Hawk (Execute) | Indiscriminate → Precise finishing |

## Risk Analysis
| Risk | Response |
|------|----------|
| Only optimal compositions used among 20 types | Differentiate effective situations by type + diversify enemy compositions |
| 40 rounds without healer in Ch1 | Sprout rear recovery + hero heal skill |
| Shroom (Summoner) neutralized by AoE | Short re-summon interval (2~3s) |
| Frog (Isolation) OP against bosses | Boss isolation resistance or reduced isolation duration |
| Hawk (Execute) clears mobs too easily | Adjust with execute threshold (30%) + cooldown |
| %Damage + Execute combo mandatory for boss fights | Balance other dealers to also be viable in boss fights |

## Implementation Scope
- **MVP**: Ch1 4 unit types, seed-cost summoning, cooldown, auto combat, deck slots, EXP+Gold acquisition, level-up UI
- **Later**: Ch2~5 16 unit types, per-chapter base stat difference balancing, purification cutscenes
