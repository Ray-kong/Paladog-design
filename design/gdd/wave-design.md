# Wave Design — Data Schema & Design Rules

## Overview

Waves are the atomic content unit of stage combat. Each round consists of
ordered waves, each wave defines a group of enemies to spawn. The system is
fully data-driven: all wave content lives in CSV tables that the game loads
at runtime and can be patched post-launch without a code update.

## Design Principles

- **Data-driven**: All wave content is CSV. No wave logic hardcoded in game code.
- **Reusable**: A wave definition can be used in multiple rounds.
- **Flexible triggers**: Each wave usage can have a different trigger type.
- **Patchable**: CSV updates can rebalance waves without a client update.
- **Trackable**: Every wave event is logged for analytics.

## Confirmed Decisions

- Enemies always spawn from the right side. No ambush/rear spawn.
- Normal rounds use the wave system. Boss rounds are handled separately.
- Trigger types: `on_clear` (next after all dead), `timer` (fixed delay),
  `hybrid` (timer but early-clear bonus) — set per wave usage, not per wave.
- Spawn patterns: `sequential` (one by one), `burst` (all at once),
  `group` (sub-groups with spacing).
- One wave can contain multiple enemy types via spawn groups.

---

## Data Tables

### Relationship Diagram

```
rounds ──1:N──> round_waves ──N:1──> waves ──N:1──> enemies
  |                                    ^
  | boss_id                            | reusable:
  v                              multiple round_waves
bosses                           can reference same wave_id
```

### 1. rounds.csv — Round Metadata

Each row = one round in the game.

| Field | Type | Description |
|-------|------|-------------|
| round_id | string | **PK**. e.g. `r_ch1_01` |
| chapter | int | Chapter number (for filtering/sorting) |
| round_num | int | Round number within chapter |
| type | enum | `normal` / `boss` |
| boss_id | string? | FK -> bosses.csv. Only when type = boss |
| unlock_unit_id | string? | Unit unlocked on clear |
| env_effect_id | string? | Environmental effect (null for Ch1) |

```csv
round_id,    chapter, round_num, type,   boss_id,         unlock_unit_id, env_effect_id
r_ch1_01,    1,       1,         normal, ,                thorn,
r_ch1_02,    1,       2,         normal, ,                ,
r_ch1_10,    1,       10,        boss,   boss_ch1_mid1,   acorn,
r_ch1_40,    1,       40,        boss,   boss_toxic_moss, snail,
r_ch2_01,    2,       1,         normal, ,                hedgie,         fog_light
```

---

### 2. round_waves.csv — Wave Assignment Per Round

Each row = one wave slot in a round. Links a round to a reusable wave definition.
Trigger settings live here (not in the wave itself) so the same wave can be
triggered differently in different rounds.

| Field | Type | Description |
|-------|------|-------------|
| round_wave_id | string | **PK**. e.g. `rw_ch1_01_w1` |
| round_id | string | FK -> rounds.csv |
| wave_id | string | FK -> waves.csv (reusable) |
| order | int | Sequence within this round (1, 2, 3...) |
| trigger_type | enum | `on_clear` / `timer` / `hybrid` |
| trigger_delay_sec | float | Delay in seconds (timer/hybrid) |

```csv
round_wave_id,  round_id,  wave_id,         order, trigger_type, trigger_delay_sec
rw_ch1_01_w1,   r_ch1_01,  wave_slime_easy, 1,     on_clear,     0
rw_ch1_01_w2,   r_ch1_01,  wave_slime_mid,  2,     on_clear,     2.0
rw_ch1_01_w3,   r_ch1_01,  wave_mixed_01,   3,     on_clear,     2.0
rw_ch1_05_w1,   r_ch1_05,  wave_slime_easy, 1,     on_clear,     0
rw_ch1_05_w2,   r_ch1_05,  wave_slime_mid,  2,     timer,        5.0
rw_ch5_38_w3,   r_ch5_38,  wave_elite_rush, 3,     timer,        3.0
```

Note: `wave_slime_easy` appears in both r_ch1_01 and r_ch1_05 — same wave
content, reused with different trigger settings.

---

### 3. waves.csv — Wave Definitions (with Spawn Data)

Each row = one spawn group within a wave. A wave with multiple enemy types
has multiple rows sharing the same wave_id.

| Field | Type | Description |
|-------|------|-------------|
| wave_id | string | Wave ID (shared across spawn groups of same wave) |
| name | string | Human-readable description |
| tag | string? | Classification (tutorial, rush, tank, mixed, elite, swarm...) |
| spawn_group | int | Group number within this wave |
| enemy_id | string | FK -> enemies.csv |
| count | int | Number of enemies |
| spawn_pattern | enum | `sequential` / `burst` / `group` |
| spacing_ms | int | Interval for sequential pattern |
| group_size | int | Sub-group size for group pattern |

```csv
wave_id,          name,                tag,      spawn_group, enemy_id,      count, spawn_pattern, spacing_ms, group_size
wave_slime_easy,  Basic slime intro,   tutorial, 1,           slime_basic,   5,     sequential,    800,        0
wave_slime_mid,   Slime medium,        normal,   1,           slime_basic,   3,     burst,         0,          0
wave_mixed_01,    Slime + ranged mix,  mixed,    1,           slime_basic,   3,     sequential,    600,        0
wave_mixed_01,    Slime + ranged mix,  mixed,    2,           slime_ranged,  2,     burst,         0,          0
wave_elite_rush,  Elite rush,          elite,    1,           root_elite,    2,     burst,         0,          0
wave_elite_rush,  Elite rush,          elite,    2,           root_swarm,    8,     group,         200,        4
```

Note: `wave_mixed_01` has two rows (spawn_group 1 and 2) — slime_basic and
slime_ranged spawn simultaneously in the same wave.

---

### 4. enemies.csv — Enemy Unit Definitions

Each row = one enemy type. Stats are placeholders for Phase 3 (numerical design).

| Field | Type | Description |
|-------|------|-------------|
| enemy_id | string | **PK** |
| name | string | Display name |
| category | enum | `normal` / `elite` |
| chapter | int | Home chapter |
| ... | | Stats added in Phase 3 |

```csv
enemy_id,      name,           category, chapter
slime_basic,   Basic Slime,    normal,   1
slime_ranged,  Ranged Slime,   normal,   1
beetle_guard,  Guard Beetle,   normal,   1
beetle_elite,  Elite Beetle,   elite,    1
root_elite,    Root Warden,    elite,    5
root_swarm,    Root Crawler,   normal,   5
```

---

### 5. bosses.csv — Boss Definitions

Boss rounds skip the wave system entirely. Pattern data to be designed separately.

| Field | Type | Description |
|-------|------|-------------|
| boss_id | string | **PK** |
| name | string | Boss name |
| boss_type | enum | `mid` / `chapter` |
| chapter | int | Home chapter |
| purify_unit_id | string? | Unit unlocked on purification (chapter bosses only) |
| ... | | Pattern data TBD |

```csv
boss_id,          name,             boss_type, chapter, purify_unit_id
boss_ch1_mid1,    Blight Sprout,    mid,       1,
boss_ch1_mid2,    Thorn Crawler,    mid,       1,
boss_ch1_mid3,    Moss Giant,       mid,       1,
boss_toxic_moss,  Toxic Moss,       chapter,   1,       snail
boss_frenzied,    Frenzied Raptor,  chapter,   2,       woody
```

---

## Game Loading Flow

```
1. Load rounds.csv → build round registry
2. For each round where type = "normal":
   a. Load round_waves.csv filtered by round_id → get wave list + triggers
   b. Load waves.csv filtered by wave_ids → get spawn definitions
   c. Load enemies.csv for referenced enemy_ids → get enemy data
3. For each round where type = "boss":
   a. Load bosses.csv by boss_id → get boss data + patterns
4. On round start:
   a. Process waves in order
   b. Apply trigger_type logic per wave
   c. Spawn enemies per spawn_group settings
```

---

## Analytics Events

| Event | Payload | Purpose |
|-------|---------|---------|
| `wave_start` | round_id, wave_id, order, timestamp | Time-per-wave tracking |
| `wave_clear` | round_id, wave_id, order, time_elapsed_ms, units_alive | Clear speed, efficiency |
| `round_start` | round_id, deck_composition, hero_skills | Session start context |
| `round_clear` | round_id, time_elapsed_ms, star_rating, sprout_hp_pct | Round-level performance |
| `player_death` | round_id, wave_id, order, sprout_hp_timeline | Death location analysis |
| `unit_summon` | round_id, wave_id, unit_id, timestamp | Player summoning patterns |
| `skill_use` | round_id, wave_id, skill_id, timestamp | Skill usage patterns |

### Key Queries Enabled

- "Which wave kills the most players?" → `player_death` grouped by wave_id
- "Is Ch3 R25 too hard?" → `round_clear` rate filtered by round_id
- "Average clear time per wave?" → `wave_clear` time_elapsed_ms aggregation
- "Most popular deck for Ch4?" → `round_start` deck_composition analysis

---

## Live-Ops Patchability

| What | How | Requires |
|------|-----|----------|
| Change enemy count in a wave | Edit waves.csv count field | CSV patch only |
| Swap enemies in a wave | Edit waves.csv enemy_id | CSV patch only |
| Change wave trigger timing | Edit round_waves.csv trigger_delay | CSV patch only |
| Add a new wave to a round | Add row to round_waves.csv + waves.csv | CSV patch only |
| Remove a wave from a round | Delete row from round_waves.csv | CSV patch only |
| Reorder waves in a round | Edit round_waves.csv order field | CSV patch only |
| Add new enemy type | Add row to enemies.csv | CSV + art asset |
| Add new spawn pattern | Add enum value to spawn_pattern | Code update |
| Add new trigger type | Add enum value to trigger_type | Code update |

---

## Still To Design (Pass 2)

- [ ] Wave tag vocabulary (full list of tags: tutorial, rush, tank, mixed, elite, swarm, ...)
- [ ] Wave pacing rules (how 5-8 waves escalate within a round)
- [ ] Per-chapter wave identity (what makes Ch3 waves feel different from Ch1)
- [ ] Elite spawn rules (when elites first appear, frequency)
- [ ] Ch1 R1-R10 reference wave table (template for all chapters)
- [ ] Enemy roster per chapter (actual enemy_id definitions)
- [ ] Difficulty scaling principles (R1→R40 within a chapter)
