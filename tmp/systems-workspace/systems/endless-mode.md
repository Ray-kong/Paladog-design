# Endless Mode

## Player Experience Goal
- A challenge mode to "test how far my deck can survive"
- Stage mode's "predetermined answer" vs Endless mode's "pushing my limits"
- Stimulates competitive drive (personal best record / leaderboard)

## Mechanic Description

### Entry Condition
- **Unlocked upon clearing Chapter 2**
- Rationale for unlock timing: Opens challenge content after the player has sufficiently understood the core systems

### Basic Structure
```
[Start] → [Wave 1] → [Wave 2] → ... → [Wave N] → [Death/Forfeit]
                                                           │
                                                    [New High Score?]
                                                           │
                                                    [Reward Settlement]
```

- Infinite wave repetition, gradual difficulty scaling
- Enemy HP/ATK increases by a fixed rate per wave (+5~8%/wave)
- Lose condition: Sprout death (same as Stage mode)

### Key Differences from Stage Mode

| Item | Stage Mode | Endless Mode |
|------|-----------|--------------|
| Goal | Clear | Survive as long as possible |
| Difficulty | Fixed (designed curve) | Infinite scaling |
| Unit Deck | Same setup each run | **Buff selection between waves** |
| Rewards | Fixed table | Proportional to waves reached |
| Play Time | 2~3 minutes | 10~30 minutes+ |

### Between-Wave Buff Selection (Roguelite Element)
- Every 5 waves cleared, **select 1 of 3 buffs**
- Buff examples:

| Category | Buff Examples |
|----------|--------------|
| Unit Enhancement | "Dealer ATK +20%" / "Tank HP +30%" |
| Hero Enhancement | "Skill cooldown -20%" / "Aura range +50%" |
| Economy | "Seed generation +30%" / "Unit cost -15%" |
| Special | "Unit revival (1 time)" / "Sprout HP recovery 20%" |

> This roguelite element is the biggest differentiator from Stage mode
> Different buff combinations each run → replay value

### Reward System
- **In-game enemy kills**: EXP (deck units) + small Gold (same as Stage mode)
- **Endless Mode exclusive rewards**: To be designed separately
- Gold diminishing returns under consideration for Endless Mode (gold per kill ↓ as waves increase, prevents infinite farming)

### Leaderboard
- **Personal best record** display (required)
- Global/friend leaderboard (future expansion)
- Weekly reset for competition cycle (future expansion)

## Connection Map
- **Unit System**: Unit level directly impacts survival wave count in Endless Mode
- **Hero System**: Skill selection/enhancement is key to high-wave survival
- **Stage Structure**: Stage progression → Endless Mode unlock, Endless Mode rewards → Assist stage progression
- **Economy**: Endless Mode as a high-efficiency farming location (but difficulty-gated)

## Risk Analysis
| Risk | Response |
|------|----------|
| Endless Mode too efficient, players skip Stage Mode | Differentiate with Stage Mode exclusive rewards (unit unlocks, story) + consider Endless Mode gold diminishing returns |
| Single session too long for mobile | Sharp difficulty spike curve after 30 minutes to naturally encourage session end |
| Specific buff combinations are overwhelmingly strong | Buff pool balancing + limit duplicate buff selection |

## Implementation Scope
- **MVP**: Infinite waves + scaling difficulty + wave-reached-based rewards
- **Later**: Roguelite buff selection, milestone rewards, leaderboard, daily rewards
