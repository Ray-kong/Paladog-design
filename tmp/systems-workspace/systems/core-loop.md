# Core Loop — Stage Play Flow

## Player Experience Goal
- "Tension from weighing two resources while managing both the front line and the hero" + "Satisfaction of units pushing forward in numbers"
- 2~3 minutes per session, short and intense repeated decision-making

## Mechanic Description

### Single Stage Flow
```
[Stage Entry]
    │
    ├─▶ [Sap auto-generation] ← Hero skill-only resource, earned over time
    ├─▶ [Seed auto-generation] ← Unit summoning-only resource, earned over time
    │
    ▼
[Player Decision-Making]
    ├─ Unit summoning (spend Seeds, cooldown)
    ├─ Hero skill usage (spend Sap, cooldown)
    └─ Hero position adjustment (front/rear)
    │
    ▼
[Combat (Auto)] ← Units auto-advance & attack
    │              Hero moves position + manual skill usage
    │              ★ Sprout (Hero) HP management required
    ▼
[Enemy Wave Cleared] ← Bonus resources on wave clear
    │
    ▼
[Boss / Final Wave]
    │
    ▼
[Win Condition: Destroy enemy base / Lose Condition: Sprout (Hero) death]
    │
    ▼
[Reward Settlement] → Gold + Hero EXP
    │
    ▼
[Return to Meta Loop] → Unit level-up (EXP+Gold) / Hero upgrade / Next stage
```

### Dual Resource System

#### Resource 1: Sap — Hero Skill Only
| Item | Value (Draft) |
|------|---------------|
| Base generation | 3 Sap per second |
| Cap | 200 Sap (prevents excessive hoarding) |
| Wave clear bonus | +20 Sap |
| Enemy kill bonus | None (time-based only) |
| In-game upgrade | Sap generation rate upgrade (purchased with Sap, escalating cost) |

- **Design Intent**: Gives rhythm to skill usage. Limited by both cooldown and resource, but guaranteed to be usable over time.
- Sap cannot be used for unit summoning, only for skills.

#### Resource 2: Seed — Unit Summoning Only
| Item | Value (Draft) |
|------|---------------|
| Base generation | 5 Seeds per second |
| Cap | None (unlimited storage) |
| Wave clear bonus | +30~50 Seeds |
| Enemy kill bonus | Small amount (+2~5 Seeds) |
| In-game upgrade | Seed generation rate upgrade (purchased with Seeds, escalating cost) |

- **Design Intent**: The core of unit quantity scaling. Enemy kill bonus allows a small snowball effect of "winning more when already winning" (but small amount).

#### Key Effect of Resource Separation
```
Before (single mana):  Summon units vs Use skills = choose only one
Now (dual resources):   Unit summoning timing + Skill usage timing = independent decisions
                        → Decision axes increased to 2
                        → Resource management complexity ↑, but frustration ↓ (eliminates "can't summon units because saving for skills" situation)
```

### Win/Lose Conditions
- **Win**: Clear all waves (normal) / Kill boss (boss fight)
- **Lose**: **Instant defeat when Sprout (Hero) HP reaches 0**
  - Even if all units are wiped out, play continues as long as Sprout is alive
  - Protecting Sprout is top priority → maximizes tension in front/rear positioning decisions
- **Star Rating**: ★ Clear / ★★ Sprout HP 50%+ / ★★★ Sprout HP 100% (no damage taken)

### Systemic Impact of Lose Condition Change
| Previous (Base HP) | Changed (Sprout Death) |
|--------------------|------------------------|
| Hero position = optional optimization | Hero position = survival-critical decision |
| Low risk for front positioning | Front positioning = high risk, high reward |
| Unit wipe = almost certain defeat | Unit wipe but Sprout alive = comeback possible |
| Encourages defensive play | Both aggressive/defensive play viable |

## Connection Map
- **Unit System**: Seeds → Unit summoning cost
- **Hero System**: Sap → Skill usage, Sprout HP = lose condition
- **Stage Structure**: Wave count/composition determines difficulty
- **Economy (Meta)**: Clear rewards → Gold → Unit level-up + Hero upgrade; In-game enemy kills → Unit EXP + small Gold

## Risk Analysis
| Risk | Response |
|------|----------|
| Two resources cause cognitive overload | Clearly separate in UI (left=unit resource, right=Sap), introduce step-by-step in tutorial |
| Greedy strategy of only upgrading Seed rate without summoning units | Early wave pressure + Sprout HP threat makes units essential |
| Sprout dies too easily causing frustration | Generous Sprout HP + rear positioning option + heal supporter units provided |
| Sprout is too hard to kill, no tension | Place Sprout-targeting attack patterns in bosses/late waves |
| Single session becomes too long | Fixed wave count (5~8), compress late wave timing |

## Implementation Scope
- **MVP**: Sap + Seed dual resources, unit summoning, auto combat, Sprout HP-based win/lose determination, 3 waves
- **Later**: Resource generation rate upgrades, star rating system, wave clear bonuses
