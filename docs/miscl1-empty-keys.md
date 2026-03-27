# MISCL1 / MISCL1AZ - Empty Key Suggestions

MISCL1 (Bepo) and MISCL1AZ (AZERTY) are the left-side symbol layers, accessed by holding `LT(MISCL1, BP_T)`. The left half is populated with programming symbols and arrows. The **entire right half is empty** (falls through to base layer via `_______`), plus several left-side positions.

## Current MISCL1 Layout Map

Empty positions marked with `[___]`:

```
Row 0 (number row):
LEFT:  [___]  |>  ~>  =>  DEG  [___]  [___]
RIGHT: [___]  [___]  [___]  [___]  [___]  [___]  [___]

Row 1 (top):
LEFT:  [___]  $  #  ->  %  `  [___]
RIGHT: [___]  [___]  [___]  [___]  [___]  [___]  [___]

Row 2 (home):
LEFT:  S(Tab)  /  *  +  =  ;
RIGHT: [___]  [___]  [___]  [___]  [___]  [___]

Row 3 (bottom):
LEFT:  Play/Pause  \  @  "  :  ~  [___]
RIGHT: [___]  [___]  [___]  [___]  [___]  [___]  [___]

Row 4 (thumb row):
LEFT:  Prev  Next  [___]  [___]  [___]
RIGHT: [___]  [___]  [___]  [___]  [___]

Thumbs: all [___]
```

**Left half:** 8 empty positions (corners, big keys, bottom row, thumbs)
**Right half:** 30 empty positions (entirely unmapped)

## Right Half Suggestions

The right half is empty because this layer is activated by holding T (right hand stays on base layer with digraph protection). But if you tap-and-release to lock the layer, the right half becomes usable.

### Option A: Programming Operators & Syntax

Mirror the left-side programming theme:

```
Row 0: [___]  &&   ||   !=   ==   ??   [___]
Row 1: [___]  <>   ::   ..   ?.   !!   [___]
Row 2:        +=   -=   *=   /=   %=   [___]
Row 3: [___]  <<   >>   **   ##   ^^   [___]
```

These could be implemented as custom keycodes or macros using `SEND_STRING()`.

### Option B: Numpad on Right

Put a numpad on the right half since you're already in a symbol context:

```
Row 0: [___]  [___]  [___]  [___]  [___]  [___]  [___]
Row 1: [___]  [___]  7      8      9      -      [___]
Row 2:        [___]  4      5      6      +      [___]
Row 3: [___]  [___]  1      2      3      =      [___]
Row 4:               0      .      [___]  [___]  [___]
```

This gives quick number access while already on the symbol layer.

### Option C: Navigation Shortcuts (IDE / Editor)

Common IDE shortcuts useful alongside symbols:

| Position | Key | Use |
|---|---|---|
| Row 2, right | `C(BP_SLSH)` | Toggle comment |
| Row 2, right | `C(BP_D)` | Duplicate line |
| Row 2, right | `C(S(BP_K))` | Delete line |
| Row 2, right | `C(BP_LBRC)` | Fold/unfold |
| Row 1, right | `C(S(BP_F))` | Find in files |
| Row 1, right | `C(BP_G)` | Go to line |

## Left Half Suggestions

### Row 0 & Row 1 Corners

| Position | Suggestion | Why |
|---|---|---|
| Row 0 left corner `[___]` | `QK_CAPS_WORD_TOGGLE` | Available while in symbol mode |
| Row 1 left corner `[___]` | `KC_GRV` x3 (triple backtick macro) | Markdown code block opener |

### Big Keys (Inner Column)

| Position | Suggestion | Why |
|---|---|---|
| Row 0 left big key `[___]` | `BP_AMPR` (`&`) | Common in code, near other operators |
| Row 0 right big key `[___]` | `BP_PIPE` (`|`) | Pipe, near other operators |
| Row 1 left big key `[___]` | `BP_EXLM` (`!`) | Logical not, near `%` and `#` |
| Row 3 left big key `[___]` | `BP_CIRC` (`^`) | XOR / exponent |

### Bottom Row & Thumbs

| Position | Suggestion | Why |
|---|---|---|
| Row 4 left `[___]` x2 | `KC_AUDIO_VOL_DOWN`, `KC_AUDIO_VOL_UP` | Near existing media keys (prev/next) |
| Row 4 left `[___]` | `KC_AUDIO_MUTE` | Complete the media cluster |
| Thumb `[___]` | Keep transparent | Thumbs stay on base layer function |

## Summary

| Priority | Suggestion | Positions |
|---|---|---|
| High | Complete missing symbols: `&` `!` `^` `|` | Left big keys |
| High | Volume controls near existing media keys | Bottom left row |
| Medium | Programming compound operators on right (`&&` `||` `!=` `+=`) | Right half rows 1-3 |
| Medium | IDE shortcuts on right | Right half home row |
| Low | Numpad on right | Right half |
| Low | Keep right half empty | If digraph protection is sufficient |

The right half being empty is intentional for the digraph protection system -- when you hold T and press a right-hand key, it sends a digraph (tc, tl, ts, etc.). Adding keys to the right half would only matter if you **lock** the layer rather than momentarily hold it.
