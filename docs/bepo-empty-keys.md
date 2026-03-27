# BEPO Layer - Empty Key Suggestions

17 key positions in the BEPO base layer are currently unmapped (`_______`). Here are suggestions for making use of them.

## Current BEPO Layout Map

Empty positions marked with `[___]`:

```
Row 0 (number row):
LEFT:  TG(FXXNPOH)  ndash  mdash  _  [___]  [___]  Delete
RIGHT: [___]  [___]  [___]  -  [___]  [___]  DF(AZERT)

Row 1 (top):
LEFT:  $  B  E'  SFT(P)  O  TD(E`/Esc)  Backspace
RIGHT: [___]  ^  TD(V/W)  SFT(D)  L  J  [___]

Row 2 (home): fully mapped - no empty positions

Row 3 (bottom):
LEFT:  RShift  CTL(A`)  Y  X  .  ALT(K)  Enter
RIGHT: [___]  ALT(')  TD(Q/Z)  G  H  RCTL(F)  C,

Row 4 (thumb row):
LEFT:  RCtrl  LGui  [___]  [___]  LT(NUMPAD,Space)
RIGHT: Space  RAlt  [___]  [___]  [___]

Thumb cluster:
LEFT:  Alt(App)  Up  |  Down  |  LShift  [___]  MO(MOUSE)
RIGHT: Right  [___]  |  Left  |  TG(GAME1)  [___]  Enter
```

## High Priority Suggestions

### QK_CAPS_WORD_TOGGLE

Auto-disabling caps lock. Turns off automatically at the end of a word (on space, punctuation). Essential for typing constants, acronyms, or uppercase French words without forgetting to toggle caps off.

**Suggested position:** Row 0 left, next to `BP_UNDS`

### QK_REP (Repeat Key)

Repeats the last pressed key. Very useful for doubled letters common in French: ll, ss, tt, nn, rr, pp, ff, mm. One tap instead of pressing the same key twice.

**Suggested position:** Row 0 right, easy reach from home row

### One-Shot Modifiers (Thumb Cluster)

Tap a modifier once, and the next key will be modified. No holding required. Reduces thumb fatigue.

```c
OSM(MOD_LCTL)   // one-shot Ctrl
OSM(MOD_LALT)   // one-shot Alt
OSM(MOD_LGUI)   // one-shot GUI/Win
```

**Suggested position:** Thumb cluster empty slots

## Medium Priority Suggestions

### Mirror Backspace / Enter (Right Big Keys)

The right-side big keys (row 1 and row 3) are empty. Adding `KC_BSPC` and `KC_ENTER` there mirrors the left side, giving both hands access to these frequent keys.

| Position | Key | Reason |
|---|---|---|
| Row 1, right big key | `KC_BSPC` | Right-hand backspace |
| Row 3, right big key | `KC_ENTER` | Right-hand enter |

### LED_LEVEL

Toggle LED brightness through 4 levels. Useful on the Shine variant.

**Suggested position:** Row 1 right corner (currently `[___]` next to `BP_J`)

### KC_APP / KC_MENU

Context menu key (right-click menu). Handy for keyboard-only workflows.

**Suggested position:** Row 4 bottom row

## Lower Priority Suggestions

### Row 0 Right - Remaining Slots

| Position | Suggestion | Why |
|---|---|---|
| Row 0, right slot 1 | `KC_INSERT` | Toggle insert mode (useful in terminals) |
| Row 0, right slot 2 | `TOGGLE_LAYER_COLOR` | Toggle RGB layer indicators (Shine) |

### Row 4 Bottom Row - Remaining Slots

| Position | Suggestion | Why |
|---|---|---|
| Bottom right slot 1 | `KC_PSCR` | Print screen |
| Bottom right slot 2 | `KC_SCRL` | Scroll lock |
| Bottom right slot 3 | `KC_NUM` | Num lock toggle |

### Thumb Cluster - Remaining Slots

| Position | Suggestion | Why |
|---|---|---|
| Left thumb [___] | `OSM(MOD_LCTL)` | One-shot Ctrl |
| Right thumb [___] top | `OSM(MOD_LALT)` | One-shot Alt |
| Right thumb [___] bottom | `KC_LGUI` | Quick access to Win/Super key |

## Summary - Recommended Assignments

The highest-value additions ranked by impact:

| Rank | Key | Impact |
|---|---|---|
| 1 | `QK_CAPS_WORD_TOGGLE` | Huge quality of life for French and code |
| 2 | `QK_REP` | Doubled letters with one tap |
| 3 | `OSM(MOD_LCTL)` on thumb | One-shot Ctrl, no holding |
| 4 | `KC_BSPC` on right big key | Symmetrical backspace access |
| 5 | `KC_ENTER` on right big key | Symmetrical enter access |
| 6 | `LED_LEVEL` | LED brightness control |
