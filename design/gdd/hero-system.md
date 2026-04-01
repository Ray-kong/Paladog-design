# Hero (Main Character) System — Sprout

## Player Experience Goal
- A sense of agency: "I am directly controlling the battlefield"
- Units are automatic, but hero skill timing creates clutch moments that turn the tide
- **"Must attack while protecting the Sprout"** — tension between survival and offense

## Mechanic Description

### Sprout Survival = Lose Condition
- **Sprout is an entity with HP. Sprout HP 0 = instant defeat.**
- Sprout HP (draft): 500 (enemy attack scales with stage difficulty)
- Sprout has a hitbox — exposed to enemy attacks when positioned at the front

### Direct Control Elements
| Control | Input Method (Mobile) | Effect |
|---------|----------------------|--------|
| **Position Movement** | Left/right screen drag or buttons | Hero moves to front/rear of the line |
| **Skill Usage** | Skill button tap | Consumes **Sap**, has cooldown |
| **Auto Attack** | Automatic | Basic attack on enemies within range |

### Position System (Front/Rear)
| Position | Advantage | Disadvantage |
|----------|-----------|-------------|
| **Front** | Aura buff applies to frontline units, participates in basic attacks | Exposed to enemy attacks → HP loss risk |
| **Rear** | Safe, natural HP recovery (1% per second) | Outside aura range, no basic attacks |

> **Core Tension**: Front positioning = combat power ↑ but death risk ↑. Knowing when to push forward and when to pull back is the skill.

### Sprout HP Management
- **Natural Recovery**: 1% HP recovery per second when positioned in rear
- **Heal Units**: Supporter units (healer type) can also heal Sprout
- **Heal Skill**: Self-heal exists among hero skills
- **Hit Invincibility**: 0.5 second invincibility after being hit (prevents consecutive hits)

### Skill Structure
- 3 slots (active skills)
- Equip method: Select 3 from owned skills before deployment
- **Resource: Sap consumption** (separate from unit summoning resource)

| Skill Type | Description | Sap Cost | Cooldown | Example |
|-----------|-------------|----------|----------|---------|
| **Offensive** | AoE/single damage | 40~60 | 8~12s | Thorn Vine Explosion (AoE damage) |
| **Buff** | Strengthens allied units | 30~50 | 10~15s | Blessing of Life (ATK +50% for 10s) |
| **Utility** | CC, heal, defense | 50~80 | 15~20s | Root Barrier (enemy movement stop for 3s), Regeneration (Sprout HP 30% recovery) |

### Growth System

#### Hero Level (Experience)
- Earn experience upon stage clear
- Level up → Small increase in HP, ATK, aura effect
- Max level cap (30~50)

#### Skill Enhancement
| Enhancement Level | Cost | Effect |
|-------------------|------|--------|
| Lv.1→2 | 200 Gold | Stats +15% |
| Lv.2→3 | 500 Gold | Stats +15%, additional effect added |
| Lv.3→4 | 1500 Gold | Stats +20% |
| Lv.4→5 (MAX) | 4000 Gold | Stats +25%, visual change |

#### Skill Unlock
- New skills unlocked through story progression / specific achievement completion
- Total skill pool: 9~12 (3~4 per type) → Equip 3

### Aura System (Passive)
- Passive buff to allied units within a certain range around the hero
- Default aura: ATK +10%
- Aura type changeable through equipment/skill tree (future expansion)
- **Only active when positioned at front** — aura deactivates in rear

## Connection Map
- **Core Loop**: Decision-making on distributing Sap to skills, Sprout HP = lose condition
- **Unit System**: Buff units via aura, heal units protect Sprout
- **Stage Structure**: Sprout-targeting attack patterns in boss fights → positioning decisions are critical
- **Endless Mode**: Sprout survival difficulty spikes sharply at high waves

## Risk Analysis
| Risk | Response |
|------|----------|
| Sprout dies too easily → frustration | Generous HP + rear natural recovery + hit invincibility frames |
| Hiding in rear only is too easy | Aura deactivation → insufficient unit DPS causes wave overflow |
| Only using skills without summoning units | Resolved by separating skill and unit resources (Sap ≠ unit resource) |
| Controls are cumbersome on mobile | Simplified to 3 skill buttons + 2-stage positioning (front/rear) |

## Implementation Scope
- **MVP**: Sprout HP + death = defeat, position movement (front/rear), 1 skill (offensive), auto attack
- **Later**: 3 skill slots, aura system, skill enhancement, level system, self-heal skill
