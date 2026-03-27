# MISCL2 / MISCL2AZ - Empty Key Suggestions

MISCL2 (Bepo) and MISCL2AZ (AZERTY) are the left-side bracket layers, accessed by holding `LT(MISCL2, BP_C)`. Only 6 keys are mapped on the left half (brackets, parens, angles, and two RALT characters). The **entire right half is empty**, and most of the left half too.

## Current MISCL2 Layout Map

Empty positions marked with `[___]`:

```
Row 0 (number row):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: [___]  [___]  [___]  [___]  [___]  [___]  [___]

Row 1 (top):
LEFT:  [___]  [___]  [___]  <-     [      ]      [___]
RIGHT: [___]  [___]  [___]  [___]  [___]  [___]  [___]

Row 2 (home):
LEFT:  [___]  [___]  [___]  [___]  (      )
RIGHT: [___]  [___]  [___]  [___]  [___]  [___]

Row 3 (bottom):
LEFT:  [___]  [___]  RALT(Y) RALT(X)  TD(</<>) TD(>/>>)  [___]
RIGHT: [___]  [___]  [___]  [___]  [___]  [___]  [___]

Row 4 + Thumbs: all [___]
```

**Mapped:** 8 keys (3 bracket pairs + `<-` arrow + 2 RALT chars)
**Empty:** ~68 positions

## Left Half Suggestions

This layer's theme is **brackets and enclosing characters**. The left half has room to complete the set.

### Row 0 - Missing Bracket-Adjacent Symbols

| Position | MISCL2 (Bepo) | MISCL2AZ (AZERTY) | Why |
|---|---|---|---|
| Row 0, pos 2 | `BP_LDAQ` (`<<`) | `FR_LDAQ` | Left guillemet alone (tap dance gives it too, but direct access) |
| Row 0, pos 3 | `BP_RDAQ` (`>>`) | `FR_RDAQ` | Right guillemet alone |

### Row 1 - Template/Generic Syntax

| Position | Suggestion | Why |
|---|---|---|
| Row 1, pos 1 | `BP_LABK` (`<`) | Standalone `<` without tap dance |
| Row 1, pos 2 | `BP_RABK` (`>`) | Standalone `>` without tap dance |

### Row 2 - Curly Braces (Missing!)

Curly braces `{}` are not on this layer -- a surprising gap for a bracket layer.

| Position | MISCL2 (Bepo) | MISCL2AZ (AZERTY) | Why |
|---|---|---|---|
| Row 2, pos 1 | `BP_LCBR` (`{`) | `FR_LCBR` | Essential for code blocks |
| Row 2, pos 2 | `BP_RCBR` (`}`) | `FR_RCBR` | Essential for code blocks |

Or place them on row 2 positions 3-4, aligned vertically with `[` `]` and `(` `)`:

```
Row 1:  [___]  [___]  [___]  <-   [   ]   [___]
Row 2:  [___]  [___]  [___]  [___] (   )
Row 3:  [___]  [___]  RALT  RALT  <   >   [___]
                                   +       +
                     add here -->  {   }
```

### Row 2 Home Row Left Side

| Position | Suggestion | Why |
|---|---|---|
| Row 2, pos 0 | `S(KC_TAB)` | Shift-Tab (already on MISCL1 but useful here too) |
| Row 2, pos 1 | `BP_LCBR` (`{`) | Curly open |
| Row 2, pos 2 | `BP_RCBR` (`}`) | Curly close |

### Row 0 - Wrap/Surround Macros

Custom macros that wrap the selection in brackets:

| Position | Macro | Output |
|---|---|---|
| Row 0, pos 4 | Wrap `()` | `Shift+Home`, type `(`, `End`, type `)` |
| Row 0, pos 5 | Wrap `[]` | Same pattern with `[` `]` |

These would need custom keycodes in `process_record_user`.

## Right Half Suggestions

Same situation as MISCL1 -- the right half is empty due to digraph protection (holding C and pressing right-hand keys sends digraphs: ch, cd, cf). Keys added here only matter if the layer is locked.

### Option A: Matching Closing Brackets

If the right half becomes usable, mirror brackets for two-hand typing:

```
Row 1: [___]  ]      }      )      >      >>     [___]
Row 2:        [      {      (      <      <<     [___]
```

### Option B: String/Quote Characters

Complement brackets with quoting characters:

| Position | Key | Why |
|---|---|---|
| Right home row | `BP_DQUO` (`"`) | Double quote |
| Right home row | `BP_QUOT` (`'`) | Single quote/apostrophe |
| Right home row | `` BP_GRV `` (`` ` ``) | Backtick |
| Right home row | `BP_TILD` (`~`) | Tilde |

## Summary

| Priority | Suggestion | Positions |
|---|---|---|
| **High** | Add curly braces `{ }` | Left home row (row 2) |
| Medium | Standalone `<` `>` without tap dance | Left row 1 |
| Medium | Standalone guillemets `<<` `>>` | Left row 0 |
| Low | Quote characters on right | Right home row (digraph caveat) |
| Low | Selection-wrap macros | Left row 0 |

The biggest gap is **curly braces `{ }`** -- essential for programming and completely absent from the bracket layer.
