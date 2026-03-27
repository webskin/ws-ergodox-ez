# MISCR2 / MISCR2AZ - Empty Key Suggestions

MISCR2 (Bepo) and MISCR2AZ (AZERTY) are the right-side selection layers, accessed by holding `LT(MISCR2, BP_COMM)`. This is MISCR1's "Shift variant" -- the right half mirrors MISCR1's navigation but with Shift held (selecting text instead of moving). Undo/Redo are on the left thumb cluster. The **entire left half is empty** except Copy/Cut, Paste, and Undo/Redo.

## Current MISCR2 Layout Map

Empty positions marked with `[___]`:

```
Row 0 (number row):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: [___]  C(Del)  C(S(Home))  C(S(Up))  C(S(End))  [___]  [___]

Row 1 (top):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: [___]  Delete  S(Home)  S(Up)  S(End)  PrtSc  [___]

Row 2 (home):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: Bksp  S(Left)  S(Down)  S(Right)  A(PrtSc)  [___]

Row 3 (bottom):
LEFT:  [___]  [___]  [___]  [___]  [___]  TD(Paste/SIns)  [___]
RIGHT: [___]  C(Bksp)  C(S(Left))  C(S(Down))  C(S(Right))  [___]  [___]

Row 4 (thumb row):
LEFT:  [___]  [___]  [___]  [___]  TD(Copy/Cut)
RIGHT: [___]  [___]  [___]  [___]  [___]

Left thumb cluster:
[___]  [___]  |  [___]  |  C(S(Z))=Redo  C(Z)=Undo  [___]

Right thumb cluster:
[___]  [___]  |  [___]  |  [___]  [___]  [___]
```

**Right half mapped:** 16 keys (selection navigation, delete, screenshots)
**Left half mapped:** 4 keys (Copy/Cut, Paste, Undo, Redo)
**Empty:** ~56 positions

## Design Observation

MISCR2 is a **selection layer** -- every right-hand navigation key is Shift-modified compared to MISCR1. This makes it natural for text editing workflows: hold comma to select, use arrows to extend selection, then Copy/Cut with left hand.

The left half is empty due to digraph protection (holding comma + right keys = digraphs like `,p`).

## Left Half Suggestions

### High Priority: Text Manipulation After Selection

You've selected text -- now what? These actions naturally follow a selection:

| Position | Key | Why |
|---|---|---|
| Row 3, pos 2 | `C(BP_D)` / `C(FR_D)` | Duplicate selection (most IDEs) |
| Row 3, pos 3 | `C(BP_L)` / `C(FR_L)` | Select entire line (VS Code) |
| Row 3, pos 4 | `KC_DELETE` | Delete selection (forward) |
| Row 2, pos 5 | `C(S(BP_K))` / `C(S(FR_K))` | Delete line (VS Code) |

### High Priority: Selection Expansion

| Position | Key | Why |
|---|---|---|
| Row 2, pos 0 | `C(S(BP_P))` | Command palette (VS Code) |
| Row 2, pos 1 | `C(BP_A)` / `C(FR_A)` | Select All |
| Row 2, pos 2 | `C(BP_D)` / `C(FR_D)` | Add next occurrence to selection (VS Code multi-cursor) |

### Medium Priority: Clipboard History / Multi-Paste

| Position | Key | Why |
|---|---|---|
| Row 1, pos 4 | `G(BP_V)` / `G(FR_V)` | Clipboard history (Win+V on Windows) |
| Row 1, pos 5 | `C(S(BP_V))` / `C(S(FR_V))` | Paste without formatting |

### Medium Priority: Move Selection (IDE)

| Position | Key | Why |
|---|---|---|
| Row 1, pos 2 | `A(KC_UP)` | Move line up (VS Code) |
| Row 1, pos 3 | `A(KC_DOWN)` | Move line down (VS Code) |
| Row 1, pos 1 | `A(S(KC_UP))` | Copy line up (VS Code) |

### Lower Priority: Multi-Cursor

| Position | Key | Why |
|---|---|---|
| Row 0, pos 1 | `C(A(KC_UP))` | Add cursor above (VS Code) |
| Row 0, pos 2 | `C(A(KC_DOWN))` | Add cursor below (VS Code) |
| Row 0, pos 3 | `C(S(BP_L))` | Select all occurrences (VS Code) |

## Right Half Suggestions

A few gaps remain on the right.

### Row 0 Left Side & Corners

| Position | Suggestion | Why |
|---|---|---|
| Row 0, pos 0 `[___]` | `C(S(KC_PGUP))` | Select page up |
| Row 0, corner `[___]` x2 | `C(S(KC_PGDN))` | Select page down |

### Row 3 Left Side & Corners

| Position | Suggestion | Why |
|---|---|---|
| Row 3, pos 0 `[___]` | `S(KC_INSERT)` | Paste from primary selection (Linux) |
| Row 3, corner `[___]` x2 | Keep transparent | Low value positions |

### Row 1 & Row 2 Right Corners

| Position | Suggestion | Why |
|---|---|---|
| Row 1, corner `[___]` | Keep `KC_PSCR` complement | Already has PrtSc nearby |
| Row 2, corner `[___]` | `C(KC_PSCR)` | Screenshot to clipboard |

## Summary

| Priority | Suggestion | Positions |
|---|---|---|
| **High** | Post-selection actions: Duplicate, Delete, Select Line | Left row 3 |
| **High** | Select All `C(A)` | Left home row |
| Medium | Multi-cursor (Ctrl+Alt+Up/Down) | Left row 0 |
| Medium | Clipboard history `Win+V` | Left row 1 |
| Medium | Move line up/down `Alt+Up/Down` | Left row 1 |
| Low | Select page up/down | Right row 0 gaps |

The biggest opportunity is turning the left half into a **post-selection action palette**: you select text with the right hand, then immediately act on it (duplicate, delete, move, multi-cursor) with the left hand -- all without leaving the layer.
