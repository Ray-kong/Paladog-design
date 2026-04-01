# Stage Structure (v1.0, Final Confirmation)

## Player Experience Goal
- "What will appear in the next round?" — Curiosity-driven progression motivation
- Boss fights every 10 rounds provide rhythmic pacing
- Long-term growth curve across 5 chapters

## Overall Structure

```
Total: 5 Chapters × 40 Rounds = 200 Rounds

Ch1 Sprout(Garden)   Ch2 Forest Beast(Forest) Ch3 Ancient Tree(Deep Forest) Ch4 Swamp(Rotten Lake) Ch5 Root(Roots of Arca)
├─ R1  [Thorn]       ├─ R1  [Hedgie]          ├─ R1  [Scorpion]            ├─ R1  [Heron]         ├─ R1  [Frog]
├─ R2~9              ├─ R2~9                   ├─ R2~9                      ├─ R2~9                ├─ R2~9
├─ R10 ★[Acorn]      ├─ R10 ★[Bee]            ├─ R10 ★[Oakguard]          ├─ R10 ★[Poison Frog]  ├─ R10 ★[Roottrap]
├─ R11~19            ├─ R11~19                 ├─ R11~19                    ├─ R11~19              ├─ R11~19
├─ R20 ★[Dandy]      ├─ R20 ★[Bear]           ├─ R20 ★[Bloom]             ├─ R20 ★[Turtle]       ├─ R20 ★[Crystal]
├─ R21~29            ├─ R21~29                 ├─ R21~29                    ├─ R21~29              ├─ R21~29
├─ R30 ★             ├─ R30 ★                  ├─ R30 ★                     ├─ R30 ★               ├─ R30 ★
├─ R31~39            ├─ R31~39                 ├─ R31~39                    ├─ R31~39              ├─ R31~39
└─ R40 ★★[Snail]     └─ R40 ★★[Woody]         └─R40 ★★[Shroom]            └─ R40 ★★[Venus]       └─R40 ★★[Hawk]
   (Toxic Moss        (Frenzied Raptor          (Toxic Mushroom              (Carnivorous Plant     (Corroded Raptor
    Purification)      Purification)             Purification)               Purification)          Purification)
```

- **Chapters**: 5
- **Rounds per Chapter**: 40
- **Boss Cycle**: R10/R20/R30 = Mid-bosses, R40 = Chapter final boss
- **Unit Unlocks**: R1 (1st), R10 (2nd), R20 (3rd), R40 (4th = boss purification)
- **R40 Boss Purification**: Purify a corrupted being → Allied unit joins (fills the chapter's missing role)

## Difficulty Curve

### Intra-Chapter Curve (Sawtooth × 4 Cycles)
```
Difficulty
  ▲
  │    ★Boss     ★Boss     ★Boss        ★★Final Boss
  │   ╱ ╲      ╱ ╲      ╱ ╲         ╱
  │  ╱   ╲    ╱   ╲    ╱   ╲       ╱
  │ ╱     ╲  ╱     ╲  ╱     ╲     ╱
  │╱       ╲╱       ╲╱       ╲   ╱
  │                            ╲ ╱
  └──────────────────────────────▶ Round
   1    10    11   20   21   30  31   40
```

### Inter-Chapter Curve
- New chapter R1 ≈ Previous chapter R25 difficulty level
- Qualitative change through new units/new enemies

## Per-Round Elements
| Element | Description |
|---------|-------------|
| Wave Count | 5 (normal) ~ 8 (boss) |
| Enemy Composition | Corrupted enemy sets by chapter theme, increasing complexity with progression |
| Environmental Effects | Ch1 none (tutorial), Ch2 fog (vision restriction), Ch3 toxic fog (sustained damage), Ch4 poison swamp (movement speed ↓), Ch5 corruption storm (periodic global damage) |
| Clear Condition | Clear all waves (normal) / Kill boss (boss fight) |

## Boss Fight Design Principles
1. **Pattern-based**: Bosses cycle through 2~3 attack patterns
2. **Sprout Targeting**: Periodically targets Sprout with direct attack patterns
3. **Skill Check**: Requires hero skill usage at specific timings
4. **Not a DPS Check**: No time limit, pattern understanding is key
5. **R40 Purification Cutscene**: Defeat → Corruption stripped away → Original form → Ally recruitment

## Star (★) System
- ★: Clear
- ★★: Sprout HP 50% or above
- ★★★: Sprout HP 100% (no damage taken)
- Cumulative stars → Chapter milestone rewards

## Round Retry
- Can retry cleared rounds
- Retry rewards: 50% Gold/EXP
- R40 boss retry motivation: To be designed separately

## Connection Map
- **Core Loop**: Each round = 1 core loop cycle
- **Unit System**: Unit unlocks at R1/R10/R20/R40 (20 types total)
- **Hero System**: Sprout survival is critical in boss fights
- **Endless Mode**: Unlocked upon Chapter 2 clear
- **Economy**: Star milestone rewards, per-round Gold/EXP

## Risk Analysis
| Risk | Response |
|------|----------|
| 200 rounds = heavy content production burden | Reuse through enemy combinations + environmental effects, only bosses are uniquely crafted |
| 40 rounds/chapter may feel tedious | Maintain motivation with boss + unit unlock every 10 rounds |
| R30~R39 feels long without rewards | Place special enemies/events, increase EXP/Gold bonuses |
| 5 chapters too long, low completion rate | Ch1~3 is main story, Ch4~5 positioned as endgame content |

## Implementation Scope
- **MVP**: Ch1 (40 rounds), 3 mid-bosses + 1 chapter boss, unit unlocks
- **Later**: Ch2~5, environmental effects, star milestones, boss purification cutscenes
