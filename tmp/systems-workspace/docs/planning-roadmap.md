# Game Design Roadmap

> Organizes all items that need to be decided during the design phase.
> Development/art production is separate. This document is for deciding "what to build."
>
> Status: ✅ Complete | 🔜 Next | ⬚ Not Started

---

## Phase 1: Core Concept — ✅ Complete

| # | Item | Decision | Status | Document |
|---|------|----------|--------|----------|
| 1.1 | Genre/Platform | Side-scrolling defense, Mobile | ✅ | game-context.md |
| 1.2 | Core Fantasy | "Become the last sprout, purify the corrupted world, and reclaim companions" | ✅ | game-context.md |
| 1.3 | Design Pillars | Strategic resource trade-offs / Unit deck building / Cute yet melancholic aesthetic | ✅ | game-context.md |
| 1.4 | Reference Games | Paladog (core loop), Clash of Clans (witch summoner type) | ✅ | game-context.md |
| 1.5 | Target Session Length | 2~3 min/stage | ✅ | game-context.md |

---

## Phase 2: Core Systems — ✅ Complete

| # | Item | Decision | Status | Document |
|---|------|----------|--------|----------|
| 2.1 | Core Loop | Seed/Sap → Summon/Skill → Auto combat → Rewards | ✅ | core-loop.md |
| 2.2 | Dual Resource System | Sap (skills) + Seed (summoning), generation rate/cap draft | ✅ | core-loop.md |
| 2.3 | Win/Lose Conditions | Sprout death = defeat, star rating system | ✅ | core-loop.md |
| 2.4 | Hero (Sprout) System | Front/rear, 3 skill slots, aura, HP management | ✅ | hero-system.md |
| 2.5 | Unit System | 20 types, 3 roles, attack type differentiation, 4~6 deck slots | ✅ | unit-system.md |
| 2.6 | Unit Level-Up | EXP+Gold based, max Lv.20, cost curve | ✅ | unit-system.md |
| 2.7 | Stage Structure | 5 chapters × 40 rounds, boss cycle, unit unlocks | ✅ | stage-structure.md |
| 2.8 | Endless Mode | Memories of Arca, infinite scaling, roguelite buffs | ✅ | endless-mode.md |
| 2.9 | UI Scene Structure | 8 scenes, transition flow, in-game UI layout | ✅ | ui-scene-structure.md |

---

## Phase 3: Numerical Design — 🔜 Next Priority

| # | Item | To Decide | Status | Priority |
|---|------|-----------|--------|----------|
| 3.1 | Unit Base Stat Table | Base HP/ATK/attack speed/range for each of 20 types. Per-chapter base stat scaling ratio (how much stronger later units are) | ⬚ | **★★★** |
| 3.2 | Unit EXP Table | Required EXP per level. EXP drop per enemy type | ⬚ | **★★★** |
| 3.3 | Enemy Stat Table | Enemy HP/ATK scaling curve per chapter/round. Normal mob/elite/boss distinction | ⬚ | **★★★** |
| 3.4 | Resource Generation Rate Balancing | Final Sap/Seed per-second generation rate. Wave clear bonuses. In-game upgrade costs | ⬚ | **★★☆** |
| 3.5 | Gold Economy Balancing | Per-round clear reward gold. Enemy kill gold (small). Level-up cost vs income curve → Expected level range per chapter | ⬚ | **★★☆** |
| 3.6 | Hero Stats/Skill Values | Sprout HP/ATK, per-skill damage/cooldown/Sap cost final values | ⬚ | **★★☆** |
| 3.7 | Difficulty Curve Simulation | Unit level vs enemy stat balance sheet. "Player may get stuck here" checkpoint verification | ⬚ | **★☆☆** |

---

## Phase 4: Content Design — ⬚ Not Started

| # | Item | To Decide | Status | Priority |
|---|------|-----------|--------|----------|
| 4.1 | Enemy Unit Design | Normal enemy types/behavior patterns per chapter. Elite enemy special abilities. Corrupted theme visual concepts | ⬚ | **★★★** |
| 4.2 | Boss Pattern Design | R10/R20/R30 mid-boss attack patterns (2~3 each). R40 chapter boss patterns + purification cutscene sequence. Ch1 boss (Toxic Moss) first | ⬚ | **★★★** |
| 4.3 | Wave Composition Table | Enemy combinations for each of 200 rounds (which enemies, how many, at what timing). Ch1 40 rounds written first | ⬚ | **★★☆** |
| 4.4 | Environmental Effect Details | Specific values and mechanics for Ch2 fog, Ch3 toxic fog, Ch4 poison swamp, Ch5 corruption storm | ⬚ | **★☆☆** |
| 4.5 | Tutorial Design | What to teach in what order during Ch1 R1~R5. Ratio of forced actions/popups/free play | ⬚ | **★★☆** |

---

## Phase 5: Hero Skill Pool Design — ⬚ Not Started

| # | Item | To Decide | Status | Priority |
|---|------|-----------|--------|----------|
| 5.1 | Skill Pool Finalization | Name/effect/type (offensive/buff/utility) for each of 9~12 skills. Design with no role overlap, like the 20 unit types | ⬚ | **★★★** |
| 5.2 | Skill Unlock Path | When each skill unlocks (story progression/achievements). Initial provided skills | ⬚ | **★★☆** |
| 5.3 | Skill Enhancement Values | Lv.1~5 enhancement costs and effects (draft exists in hero-system.md, final confirmation needed) | ⬚ | **★☆☆** |

---

## Phase 6: Meta/Economy Systems — ⬚ Not Started

| # | Item | To Decide | Status | Priority |
|---|------|-----------|--------|----------|
| 6.1 | Endless Mode Reward Design | Existing rewards deleted. Redesign rewards per waves reached | ⬚ | **★★☆** |
| 6.2 | Endless Mode Roguelite Buff Pool | "Legacy of the Predecessor Guardians" full buff list. Balance per category. Duplicate selection rules | ⬚ | **★★☆** |
| 6.3 | R40 Boss Retry Motivation | Replacement reward/motivation design after material removal (PD to fill separately) | ⬚ | **★★☆** |
| 6.4 | Deck Slot Expansion | Finalize 4→6 slot expansion conditions/timing (which chapter, what conditions) | ⬚ | **★☆☆** |
| 6.5 | Star Milestone Rewards | Reward table based on cumulative stars | ⬚ | **★☆☆** |
| 6.6 | Monetization Model | Ad/in-app purchase methods, what to sell (skins? convenience?) | ⬚ | **★☆☆** |

---

## Phase 7: Story/Narrative Integration — ⬚ Not Started

| # | Item | To Decide | Status | Priority |
|---|------|-----------|--------|----------|
| 7.1 | Per-Chapter Story Outline | Story flow for each chapter: start → development → boss → purification. Corruption mystery breadcrumb placement | ⬚ | **★★☆** |
| 7.2 | Story Delivery Method | Cutscenes? Dialogue? Environmental storytelling? What format before/after chapter starts/boss fights | ⬚ | **★☆☆** |
| 7.3 | Per-Unit Background Lore | Short lore for each of 20 types (5 purification units have pre/post corruption stories) | ⬚ | **★☆☆** |

---

## Recommended Work Order

```
[Current Position]
    │
    ▼
Phase 3.1~3.3: Unit/Enemy Base Stats + EXP Table
    │  ← Without this, remaining numerical design is impossible
    ▼
Phase 4.1~4.2: Enemy Unit Design + Ch1 Boss Patterns
    │  ← Directly tied to prototype
    ▼
Phase 5.1: Hero Skill Pool Finalization
    │  ← Completes in-game decision-making axes
    ▼
Phase 4.3 + 4.5: Ch1 Wave Composition + Tutorial
    │  ← Required for Ch1 prototype completion
    ▼
Phase 3.4~3.6: Resource/Gold/Hero Value Balancing
    │  ← Adjust after prototype playtesting
    ▼
Phase 6: Meta System Details
    │
    ▼
Phase 7: Story Details
```

**Top Priority Items Ready for Immediate Work:**
1. **Unit Base Stat Table** (3.1) — Foundation of the level-up system
2. **Enemy Unit Design** (4.1) — Enemies are needed for combat to function
3. **Ch1 Boss Patterns** (4.2) — Core of the MVP prototype
