# Decision Log

> Records major project decisions in chronological order.
> The PD bot adds entries here after receiving Director approval.

---

### [2026-03-22] [Genre/Platform] Side-scrolling Defense, Mobile Confirmed
- **Decision**: Paladog-style side-scrolling defense game, targeting mobile
- **Rationale**: Director's instruction. Stage-based + endless mode structure
- **Impact**: game-context.md basic info update
- **Status**: Finalized

### [2026-03-22] [Worldbuilding] Edena/Arca/Great Blight Worldview Confirmed
- **Decision**: World Tree Arca, continent of Edena corroded by Blight, set in the Last Garden. Enemies are corrupted former allies.
- **Rationale**: Narrative bot draft + Systems bot cross-check, then Director approval
- **Impact**: game-context.md worldbuilding section, narrative-workspace/lore/
- **Status**: Finalized

### [2026-03-22] [System] Dual Resource System — Sap + Seed
- **Decision**: Sap = for Sprout skills, Seed = for unit summoning. References Paladog's mana/food structure.
- **Rationale**: Director's instruction. Separate skill resource and summoning resource like Paladog.
- **Impact**: game-context.md core systems, systems-workspace/systems/
- **Status**: Finalized

### [2026-03-22] [System] Defeat Condition — Sprout Death = Round Loss
- **Decision**: Instead of base HP, defeat occurs when main character (Sprout) dies. Sprout is the last seedling of Arca, irreplaceable.
- **Rationale**: Director's instruction. Hero immortality setting revoked.
- **Impact**: game-context.md core loop, hero system lore revision
- **Status**: Finalized

### [2026-03-22] [System] 20 Units Finalized
- **Decision**: No elemental rock-paper-scissors; differentiated by attack type only. Every unit has a unique role (no overlap). 20 attack types: Dealer 8 (basic melee/ranged/AoE/multi-strike/%HP damage/DoT/piercing/isolate+continuous DPS/execute), Tank 5 (HP tank/taunt/knockback/shield/reflect), Support 7 (healer/buffer/slow/summoner/debuffer/stun). Implementation constraints: enemy-attaching units prohibited, ground-placement units prohibited.
- **Rationale**: Director-led redesign. Removed role overlap + verified implementation feasibility. Deleted self-destruct/resource-generator/moss/leech/mistletoe, replaced with snail/poison frog/scorpion/frog/hawk.
- **Impact**: game-context.md unit system full rewrite
- **Status**: Finalized

### [2026-03-22] [System] Boss Purification → Unit Unlock System
- **Decision**: Defeating a chapter boss triggers purification cutscene → unlocks as ally unit. Purified unit upgrade materials drop from rematching that boss.
- **Rationale**: Systems bot proposal + Narrative bot strong endorsement. Adds emotional weight to unit unlocks.
- **Impact**: game-context.md stage structure, unit system
- **Status**: Finalized

### [2026-03-22] [System] Endless Mode — "Memories of Arca"
- **Decision**: Set as reliving Arca's past memories. Roguelite buffs = "Legacy of Previous Guardians". MVP reuses existing Blighted enemy assets.
- **Rationale**: Narrative bot Plan B proposal + Systems bot agreement. Differentiates tone from stages + lore expandability.
- **Impact**: game-context.md endless mode, systems-workspace/systems/endless-mode
- **Status**: Finalized

### [2026-03-22] [System] Unit Family = Unlock Tier, Role = Combat Function Separation
- **Decision**: Family represents chapter-based unlock order. Tank/Dealer/Support roles are combat functions.
- **Rationale**: Systems/Narrative bot consensus. Prevents tutorial information overload.
- **Impact**: game-context.md unit system
- **Status**: Finalized

### [2026-03-22] [System] Stage Structure Change — 5 Chapters x 40 Rounds
- **Decision**: 5 chapters x 40 rounds = 200 rounds. R10/R20/R30 mid-bosses, R40 chapter boss. Unit unlocks at R1/R10/R20/R40 (4 per chapter). R40 boss = Blighted version of the unlock unit, compensating for that chapter's missing role.
- **Rationale**: Director's instruction. Expanded from previous 10-round structure.
- **Impact**: game-context.md stage structure full rewrite
- **Status**: Finalized

### [2026-03-22] [System] Unit Placement Principles
- **Decision**: R1 first unit must be a dealer. No healer placed in Chapter 1. No unit role overlap allowed.
- **Rationale**: Director's instruction. If the first unit is a tank there's no damage, and a Ch1 healer is overpowered.
- **Impact**: Unit chapter-by-chapter placement
- **Status**: Finalized

### [2026-03-22] [System] Summoner Unit Added (Clash of Clans Witch Style)
- **Decision**: Support unit that continuously summons mini units with 1 HP. References Clash of Clans Witch.
- **Rationale**: Director's instruction.
- **Impact**: Included in confirmed attack types
- **Status**: Finalized

### [2026-03-22] [System] Implementation Constraints Established + 5 Units Deleted/Replaced
- **Decision**: Units that attach to enemies and ground-placement units deleted as infeasible. Self-destruct deleted by Director judgment, resource-generator deleted as balance-breaking. 5 deleted (moss/leech/mistletoe/seed bomb/seed pouch) → 5 replacements (snail/poison frog/scorpion/frog/hawk).
- **Rationale**: Director's instruction. Based on visual implementation feasibility and balance criteria.
- **Impact**: game-context.md unit system, implementation constraints section added
- **Status**: Finalized

### [2026-03-22] [System] Unit Level-Up System Introduced — Replaces 5-Stage Meta Upgrade
- **Decision**: Deleted existing "5-stage meta upgrade (gold+materials)". Replaced with new level-up system: in-game enemy kills → earn EXP (deck units only) + gold, level up outside of gameplay via UI when EXP threshold met + gold spent, simple stat increase, max Lv.20. Steep cost curve at later levels provides economic incentive to recruit new units. No artificial systems like catch-up EXP — balanced naturally by higher base stats of later chapter units.
- **Rationale**: PD decision. Removes material farming burden for solo developer + improves growth granularity.
- **Impact**: unit-system.md upgrade section full rewrite, core-loop.md reward flow revision, endless-mode.md rewards removed, stage-structure.md R40 material drops removed, game-context.md unit system revision
- **Status**: Finalized

### [2026-03-22] [System] UI Scene Structure Confirmed
- **Decision**: 8-scene structure confirmed — Title, Main Lobby (Hub), Stage Select, Pre-battle Prep, In-game, Results Screen, Unit Management, Deck Building. Hub structure reachable within 2 taps. Pre-battle Prep scene shared between stages/endless mode. Results screen shows per-unit EXP + unlock/purification cutscene.
- **Rationale**: PD decision.
- **Impact**: systems-workspace/systems/ui-scene-structure.md newly created
- **Status**: Finalized

### [2026-03-22] [System] Frog — New Isolate+Continuous DPS Type Introduced
- **Decision**: Grabs 1 enemy with tongue and chews (continuous DPS); spits out if not killed. A new isolate+DPS hybrid type that didn't exist before. Placed at Ch5-R1.
- **Rationale**: Director's idea. Extended from Clash of Clans Witch reference.
- **Impact**: Ch5 first unit
- **Status**: Finalized

### [2026-03-22] [System] Hawk — Execute Dealer Final Unit Confirmed
- **Decision**: Deals bonus damage when enemy HP is below a certain %. Paired with Venus Flytrap (%HP shred) for "shred+finish" synergy. Ch5-R40 boss purification unit.
- **Rationale**: Unanimous recommendation from Narrative/Systems bots + Director approval.
- **Impact**: All 20 units finalized
- **Status**: Finalized
