# Systems Map

> Master index of all game systems. Each system has an ID, one-line description,
> design status, and dependency list. Use this to track what exists, what needs
> design, and what blocks what.
>
> Status: ✅ Designed | ⬚ Not Started

---

## A. Core Systems — ✅ Designed

| ID | System | Description | Dependencies | Document |
|----|--------|-------------|--------------|----------|
| A1 | Core Loop | Dual resources (Sap/Seed), combat flow, win/lose conditions | — | core-loop.md |
| A2 | Hero (Sprout) | Front/rear positioning, 3 skill slots, aura, HP = lose condition | A1 | hero-system.md |
| A3 | Unit System | 20 types, 3 roles, deck (4-6 slots), EXP+Gold level-up, max Lv.20 | A1 | unit-system.md |
| A4 | Stage Structure | 5 chapters × 40 rounds, boss cycle, unit unlocks, star rating | A1, A3 | stage-structure.md |
| A5 | Endless Mode | "Memories of Arca", infinite scaling, roguelite buffs, Ch2 unlock | A1, A3 | endless-mode.md |
| A6 | UI Scene Structure | 8 scenes, hub navigation, 2-tap reach, mobile-optimized | All | ui-scene-structure.md |

---

## B. Combat Content — ⬚ Not Started

| ID | System | Description | Dependencies |
|----|--------|-------------|--------------|
| B1 | Enemy System | Normal / Elite / Boss categories, per-chapter behavior themes | A4 |
| B2 | Boss Patterns | R10/R20/R30 mid-boss + R40 chapter boss attack patterns | B1 |
| B3 | Hero Skill Pool | Full 9-12 skill definitions — name, type, effect, no role overlap | A2 |
| B4 | Environmental Effects | Ch2 fog, Ch3 toxic fog, Ch4 poison swamp, Ch5 corruption storm | A4, B1 |
| B5 | Wave Design | Wave types, composition rules, pacing, elite spawn rules | B1, B4 |

---

## C. Hero Expansion — ⬚ Not Started

| ID | System | Description | Dependencies |
|----|--------|-------------|--------------|
| C1 | Hero Equipment / Items | Accessories, relics, aura modifiers, stat bonuses for Sprout | A2 |
| C2 | Hero Skins | Cosmetic appearance changes for Sprout | A2 |

---

## D. Economy & Shop — ⬚ Not Started

| ID | System | Description | Dependencies |
|----|--------|-------------|--------------|
| D1 | Currency System | Currency types beyond Gold (premium currency, tokens, etc.) | A1 |
| D2 | Shop | What is sold, which currencies, storefront UI | D1, C1, C2 |
| D3 | Monetization Model | Ads, IAP, F2P ceiling, pay-to-win boundary | D1, D2 |
| D4 | Stamina / Energy | Play session limiter — whether it exists and how it works | A4, A5 |

---

## E. Progression Systems — ⬚ Not Started

| ID | System | Description | Dependencies |
|----|--------|-------------|--------------|
| E1 | Achievements | Goals, tracking, rewards | All |
| E2 | Collection / Bestiary | Unit, enemy, and lore entries for viewing | A3, B1 |
| E3 | Daily / Weekly Missions | Recurring objectives with rewards | D1 |
| E4 | Login Rewards | Daily attendance rewards, cumulative bonuses | D1 |
| E5 | Deck Slot Expansion | Conditions for expanding 4 → 5 → 6 slots | A3, A4 |
| E6 | Star Milestone Rewards | Reward tiers based on cumulative stars earned | A4 |

---

## F. Social — ⬚ Not Started

| ID | System | Description | Dependencies |
|----|--------|-------------|--------------|
| F1 | Leaderboard | Endless mode rankings (personal best, global, friends) | A5 |
| F2 | Friends / Guild | Social connections, sharing, cooperative features | — |
| F3 | PvP | Player vs player mode (async? real-time? deck-based?) | A3, B3 |

---

## G. Narrative — ⬚ Not Started

| ID | System | Description | Dependencies |
|----|--------|-------------|--------------|
| G1 | Chapter Story Outlines | Per-chapter story arc, Blight mystery breadcrumbs | A4, B2 |
| G2 | Story Delivery Method | Cutscene, dialogue, environmental storytelling format | G1 |

---

## Dependency Graph

```
A1 Core Loop
├── A2 Hero ─────────── B3 Skill Pool
│                  ├── C1 Equipment
│                  └── C2 Skins
├── A3 Units ────────── E5 Deck Slots
│                  └── E2 Collection
├── A4 Stages ───────── B1 Enemies ──── B2 Boss Patterns
│         │                        ├── B4 Env Effects
│         │                        └── E2 Collection
│         ├── B4 ─┐
│         │       └── B5 Wave Design
│         ├── E6 Star Milestones
│         └── D4 Stamina
├── A5 Endless ──────── F1 Leaderboard
│         └── D4 Stamina
├── D1 Currency ─────── D2 Shop ────── D3 Monetization
│                  ├── E3 Missions
│                  └── E4 Login Rewards
├── E1 Achievements (depends on all)
├── F2 Friends / Guild (independent)
├── F3 PvP (A3, B3)
└── G1 Story (A4, B2) ── G2 Delivery
```

---

## Summary

| Category | Count | Status |
|----------|-------|--------|
| A. Core | 6 | ✅ All designed |
| B. Combat Content | 5 | ⬚ Not started |
| C. Hero Expansion | 2 | ⬚ Not started |
| D. Economy & Shop | 4 | ⬚ Not started |
| E. Progression | 6 | ⬚ Not started |
| F. Social | 3 | ⬚ Not started |
| G. Narrative | 2 | ⬚ Not started |
| **Total** | **28** | **6 done / 22 remaining** |
