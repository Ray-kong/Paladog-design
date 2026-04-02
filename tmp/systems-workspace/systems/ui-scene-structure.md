# UI Scene Structure (v1.0)

## Player Experience Goal
- "Reach any destination within 2 taps from anywhere" — Mobile-optimized navigation
- Minimize friction to battle entry (Lobby → Deployment Prep → In-Game = 3 steps)
- Clear separation between meta loop (level-up/deck building) and core loop (combat)

## Scene List

### 1. Title
- Game logo + "Tap to Start"
- Server connection / Data loading
- → Transitions to **Main Lobby**

### 2. Main Lobby
- Hub for all menus
- Accessible menus:
  - Stage Select
  - Endless Mode Entry (unlocked after Ch2 clear)
  - Unit Management
  - Deck Building
  - Hero Skill Equip
  - Settings

### 3. Stage Select
- Chapter map (Ch1~5, locked/unlocked display)
- Round list (R1~R40, clear status + star rating display)
- Boss round highlighting (R10/R20/R30/R40)
- Round selection → Transitions to **Deployment Prep**

### 4. Deployment Prep
- Current deck display (4~6 unit slots)
- Deck modification available (direct editing here)
- Sprout equipped skills confirmation
- Enemy info preview (enemy composition hints)
- [Deploy] button → Transitions to **In-Game**

### 5. In-Game (Combat)
- Side-scrolling combat screen
- **Bottom UI**:
  - Unit summon buttons (4~6 deck slots, Seed cost + cooldown display)
  - Sprout skill buttons (3 buttons, Sap cost + cooldown display)
- **Top UI**:
  - Sap gauge
  - Seed gauge
  - Wave progress display
  - Sprout HP bar
- **Sprout Position Movement**: Front/rear toggle (drag or button)
- Combat end → Transitions to **Result Screen**

### 6. Result Screen
- Victory/Defeat display
- Star rating (★★★)
- Gold earned
- Per-unit EXP earned (deck units only, individual EXP bar display)
- **Special Cutscenes**:
  - Unit unlock (R1/R10/R20): New unit appearance cutscene
  - Boss purification (R40): Corruption stripped away → Original form → Ally recruitment cutscene
- [Next] → **Main Lobby** (or shortcut to next round)

### 7. Unit Management
- Unit list (locked/unlocked distinction)
- Unit details:
  - Current level, stats (ATK/HP, etc.)
  - EXP bar (current/required)
  - [Level Up] button (active when EXP met + sufficient Gold)
  - Level-up cost display (Gold)
- Unit info: Role, type, attack method description

### 8. Deck Building
- 4~6 slots (expands with progression)
- Place from owned unit list via drag/tap
- Duplicate unit placement ❌
- Unit level + stat summary display
- Deck total combat power display (for reference)

## Scene Transition Flow

```
[Title]
    │
    ▼
[Main Lobby] ◄─────────────────────────────────┐
    │                                          │
    ├──▶ [Stage Select] ──▶ [Deployment Prep] ──▶ [In-Game] ──▶ [Result Screen] ──┤
    │                           ▲                                                  │
    ├──▶ [Endless Mode Entry] ──┘  (shares Deployment Prep)                        │
    │                                                                              │
    ├──▶ [Unit Management] ────────────────────────────────────────────────────────►┤
    │                                                                              │
    ├──▶ [Deck Building] ──────────────────────────────────────────────────────────►┤
    │                                                                              │
    ├──▶ [Hero Skill Equip] ───────────────────────────────────────────────────────►┤
    │                                                                              │
    └──▶ [Settings] ───────────────────────────────────────────────────────────────┘
```

### Transition Matrix

| From \ To | Title | Lobby | Stage Select | Deploy Prep | In-Game | Result | Unit Mgmt | Deck Build | Hero Skill | Settings |
|-----------|-------|-------|-------------|-------------|---------|--------|-----------|------------|------------|----------|
| **Title** | - | ✅ | | | | | | | | |
| **Lobby** | | - | ✅ | | | | ✅ | ✅ | ✅ | ✅ |
| **Stage Select** | | ✅ | - | ✅ | | | | | | |
| **Deploy Prep** | | | ✅ | - | ✅ | | | | | |
| **In-Game** | | | | | - | ✅ | | | | |
| **Result** | | ✅ | | ✅* | | - | | | | |
| **Unit Mgmt** | | ✅ | | | | | - | | | |
| **Deck Build** | | ✅ | | | | | | - | | |
| **Hero Skill** | | ✅ | | | | | | | - | |
| **Settings** | | ✅ | | | | | | | | - |

*Result → Deploy Prep: "Next Round" shortcut (optional)

### Endless Mode Transition
- Endless Mode Entry → **Deployment Prep** (skips Stage Select)
- Deployment Prep scene is shared between Stage/Endless modes (distinguished by mode flag)

## Connection Map
- **Core Loop**: Deployment Prep → In-Game → Result = 1 core loop cycle
- **Unit System**: Level up in Unit Management scene, select for deployment in Deck Building scene
- **Hero System**: Select 3 skills in Hero Skill Equip scene
- **Stage Structure**: Select chapter/round in Stage Select scene
- **Endless Mode**: Direct entry from Lobby to Deployment Prep

## Risk Analysis
| Risk | Response |
|------|----------|
| Too many scenes makes navigation complex | Hub structure from Lobby guarantees reaching any destination within 2 taps |
| Deploy Prep → In-Game transition is slow | Async loading during Deploy Prep, instant transition on button press |
| Player drops off at Result Screen | "Next Round" shortcut encourages continuous play |
| Separating Unit Management/Deck Building causes confusion | Unit Management = Growth (level-up), Deck Building = Deployment composition — clear role separation |
| Too many in-game UI elements (summon+skill+resources+HP) | Controls on bottom, info on top for area separation + mobile thumb zone consideration |

## Implementation Scope
- **MVP**: Title, Lobby (Stage Select + Unit Management + Deck Building only), Deployment Prep, In-Game, Result Screen
- **Later**: Endless Mode Entry, Hero Skill Equip, Settings, Result Screen special cutscenes (purification), Next Round shortcut
