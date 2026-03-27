# GAME1 - Empty Key Suggestions

The GAME1 layer is a Call of Duty gaming layout, toggled via `TG(GAME1)`. The **left hand is the primary gaming hand** (movement, actions, weapons). The right hand is rarely used (rests on the mouse). Right-side keys serve mainly as a fallback for typing in chat.

## Current GAME1 Layout Map

Empty positions marked with `[___]`, blocked keys with `[NO]`:

```
Row 0 (number row):
LEFT:  #  KP_1  KP_2  KP_3  KP_4  KP_5  Delete
RIGHT: [___]  [___]  [___]  -  [___]  [___]  [___]

Row 1 (top):
LEFT:  $  B  E'  P  O  TD(E`/Esc)  Backspace
RIGHT: [___]  ^  TD(V/W)  SFT(D)  L  J  [___]

Row 2 (home):
LEFT:  Tab  A  U  I  E  ,
RIGHT: LT(MISCL2,C)  LT(MISCL1,T)  S  R  N  M

Row 3 (bottom):
LEFT:  RShift  A`  Y  X  .  K  Enter
RIGHT: [___]  ALT(')  TD(Q/Z)  G  H  RCTL(F)  RCTL(C,)

Row 4 (thumb row):
LEFT:  RCtrl  KP_6  KP_7  KP_8  Space
RIGHT: Space  RAlt  [___]  [___]  [___]

Left thumb cluster:
[NO]  Up  |  Down  |  LShift  L  KP_0

Right thumb cluster:
[NO]  [NO]  |  [NO]  |  TG(GAME1)  [NO]  Enter
```

**Design:** Left side is Bepo-based with number row replaced by KP_1-8 for weapon slots. Home row keeps Bepo letters for chat. Thumb has Shift + L (lean?) + KP_0.

## Left Half Suggestions (Gaming Hand)

### Row 0 - Weapon/Item Slots

Already has KP_1 through KP_5 for weapon switching. Consider:

| Position | Current | Suggestion | Why |
|---|---|---|---|
| Row 0, pos 0 (`#`) | `BP_HASH` | `KC_GRV` or `` ` `` | Console toggle (common in FPS games) |
| Row 0, big key | `KC_DELETE` | `KC_TAB` | Scoreboard (Tab is standard in CoD) |

### Row 1 - Quick Actions

| Position | Current | Suggestion | Why |
|---|---|---|---|
| Row 1, big key | `KC_BSPC` | `BP_G` or mapped grenade key | Grenade / tactical -- needs quick access |

### Row 3 - Stance & Actions

Row 3 is good for crouch/prone since your pinky rests there.

| Position | Current | Could also be |
|---|---|---|
| Row 3, pos 0 (`KC_RSFT`) | Right Shift | Sprint (Shift is standard for sprint in CoD) -- already correct |
| Row 3, big key (`KC_ENTER`) | Enter | Chat open -- already correct |

### Row 4 - Bottom Row

| Position | Current | Suggestion | Why |
|---|---|---|---|
| Row 4, pos 0 (`KC_RCTL`) | Right Ctrl | `KC_LCTL` | Crouch (Ctrl is standard in CoD) -- use LCTL for consistency |
| Row 4, pos 1 (`KP_6`) | KP_6 | Keep or map to killstreak slot | Extra weapon/killstreak slot |

### Thumb Cluster - Critical Gaming Keys

| Position | Current | Suggestion | Why |
|---|---|---|---|
| Left thumb, pos 0 (`KC_LSFT`) | Left Shift | Sprint -- already good |
| Left thumb, pos 1 (`BP_L`) | L | Lean left? Consider `KC_Q` | Standard lean in CoD |
| Left thumb, pos 2 (`KC_KP_0`) | KP_0 | Lean right? Consider `KC_E` | Standard lean in CoD |

### Arrow Keys (Inner Thumb)

| Position | Current | Why it's there |
|---|---|---|
| Up | `KC_UP` | Menu navigation |
| Down | `KC_DOWN` | Menu navigation |

These are fine for in-game menu navigation.

## Right Half Suggestions (Rarely Used)

Since the right hand is on the mouse, right-side keys are mostly for **chat typing** and **between-round actions**.

### High Priority: Chat Essentials

The right half already inherits Bepo letters for chat. A few additions:

| Position | Suggestion | Why |
|---|---|---|
| Row 0, right corner `[___]` | `TG(GAME1)` | Duplicate exit to GAME1 -- easy to find when needing to leave |
| Row 1, right corner `[___]` | `KC_ESC` | Escape -- pause menu, cancel |
| Row 3, right big key `[___]` | `KC_ENTER` | Chat send -- confirm message |

### Medium Priority: Voice/Communication

| Position | Suggestion | Why |
|---|---|---|
| Row 0, right pos 1 `[___]` | `KC_F1` | Push-to-talk (if bound to F1 in game) |
| Row 0, right pos 2 `[___]` | `KC_F2` | Team chat toggle |

### Low Priority: Right Side Cleanup

| Position | Suggestion | Why |
|---|---|---|
| Row 4, right `[___]` x3 | Keep transparent | Never reached during gameplay |
| Right thumb `[NO]` keys | Keep blocked | Prevents accidental presses |

## CoD-Specific Bindings Reference

Standard Call of Duty PC keybinds (for reference when mapping):

| Action | Standard Key | Position on GAME1 |
|---|---|---|
| Move Forward | W | Bepo: mapped via OS layout |
| Move Back | S | Bepo: mapped via OS layout |
| Move Left | A | Bepo: mapped via OS layout |
| Move Right | D | Bepo: mapped via OS layout |
| Sprint | Shift | Left thumb (LShift) |
| Crouch | Ctrl | Row 4 pos 0 (RCtrl) |
| Prone | Z | Row 3 (mapped via Bepo) |
| Jump | Space | Row 4 pos 4 + right thumb |
| Reload | R | Home row right (via Bepo) |
| Interact | F | Row 3 right (RCTL_T(BP_F)) -- **caution**: mod-tap may interfere |
| Weapon Switch | 1-5 | Row 0 KP_1 to KP_5 |
| Grenade | G | Not easily accessible on left |
| Tactical | Q | Not easily accessible on left |
| Scoreboard | Tab | Row 2 pos 0 (KC_TAB) |
| Console | `` ` `` | Not mapped |
| Melee | V | Not easily accessible on left |
| Map | M | Home row right |

## Key Concerns

### Mod-Tap on RCTL_T(BP_F)

`RCTL_T(BP_F)` on row 3 sends F on tap but Ctrl on hold. In fast gaming, the 200ms tapping term delay before F registers could be a problem for the Interact/Use key. Consider replacing with plain `BP_F` on this layer.

### Mod-Tap on RCTL_T(BP_CCED)

Same concern -- if C-cedilla is used for a game action, the Ctrl hold behavior adds latency.

### TD(TD_EGRV_ESC) for Escape

Tap dance on Escape adds delay. In gaming, Escape needs to be instant (pause menu). Consider replacing with plain `KC_ESC` on this layer.

## Summary

| Priority | Suggestion | Position |
|---|---|---|
| **High** | Replace `TD(TD_EGRV_ESC)` with `KC_ESC` | Row 1 pos 5 -- instant Escape |
| **High** | Replace `RCTL_T(BP_F)` with `BP_F` | Row 3 -- remove mod-tap delay on Interact |
| **High** | Add `KC_GRV` (console) | Row 0 pos 0 |
| **High** | Map scoreboard to `KC_TAB` on big key | Row 0 big key (replace Delete) |
| Medium | Add grenade/tactical key on left | Row 1 big key |
| Medium | Add `TG(GAME1)` exit on right corner | Row 0 right corner |
| Medium | Add `KC_ESC` on right side | Row 1 right corner |
| Low | Remove all mod-taps and tap dances on left | Reduce input latency across the layer |

The biggest issues are **mod-tap and tap dance latency** -- gaming needs instant key registration. Consider replacing all `SFT_T()`, `RCTL_T()`, `ALT_T()`, and `TD()` with plain keycodes on this layer.
