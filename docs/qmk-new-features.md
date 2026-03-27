# QMK New Features (2019-2026)

Major QMK features added in the last 7 years, relevant to this ErgoDox EZ setup with 14 layers, home row mods, tap dance, and French Bepo/AZERTY layouts.

## High Impact

### Chordal Hold (2025)

"Opposite hands" rule for mod-taps. If you press a mod-tap key and another key on the **same hand**, it registers as a tap. Different hands = hold. Dramatically reduces accidental modifier triggers on home row mods (`CTL_T()`, `SFT_T()`, `ALT_T()`).

Official successor to the community Achordion library. Supports multi-mod combinations within the tapping term (e.g., Ctrl+Shift+V).

```c
// In rules.mk
CHORDAL_HOLD_ENABLE = yes
```

[Documentation](https://docs.qmk.fm/tap_hold#chordal-hold)

### Caps Word

Activates caps lock that **automatically turns off** at the end of a word (on space, punctuation, etc.). No more forgetting to toggle caps off.

```c
// Assign to a key
QK_CAPS_WORD_TOGGLE
```

[Documentation](https://docs.qmk.fm/features/caps_word)

### Repeat Key

Repeats the last pressed key. Useful for doubled letters in French (ll, ss, tt). Also has an alternate repeat variant.

```c
// Assign to a key
QK_REP           // repeats last key
QK_AREP          // alternate repeat (e.g., if last was 'n', sends 'u')
```

[Documentation](https://docs.qmk.fm/features/repeat_key)

### Key Overrides

Remap what Shift+key (or any modifier+key) produces. Customize shifted behavior per key without complex `process_record_user` logic.

```c
// Make Shift+. produce ? instead of >
const key_override_t dot_override = ko_make_basic(MOD_MASK_SHIFT, KC_DOT, KC_QUES);
```

[Documentation](https://docs.qmk.fm/features/key_overrides)

### OS Detection

Auto-detects Windows, macOS, Linux, or iOS at USB connect. Could replace manual Mac vs PC shortcut switching.

```c
os_variant_t os = detected_host_os();
if (os == OS_MACOS) {
    // use GUI-based shortcuts
} else {
    // use Ctrl-based shortcuts
}
```

[Documentation](https://docs.qmk.fm/features/os_detection)

## Medium Impact

### Combos Overhaul

Completely rewritten. Zero RAM overhead (was a concern on m32u4). Works by key position instead of keycode, so combos work correctly across layers. Much faster than 7 years ago.

```c
// Press J+K simultaneously to get Escape
const uint16_t PROGMEM jk_combo[] = {KC_J, KC_K, COMBO_END};
combo_t key_combos[] = {
    COMBO(jk_combo, KC_ESC),
};
```

[Documentation](https://docs.qmk.fm/features/combo)

### Custom Shift Keys

Define `normal_keycode` + `shifted_keycode` per key. Simpler than switch cases for custom shift behavior.

```c
const custom_shift_key_t custom_shift_keys[] = {
    {KC_DOT, KC_QUES},   // Shift+. = ?
    {KC_COMM, KC_EXLM},  // Shift+, = !
};
```

[Documentation](https://docs.qmk.fm/features/custom_shift_keys)

### Autocorrect

Built-in typo correction. Define a dictionary of common mistakes, runs automatically as you type.

[Documentation](https://docs.qmk.fm/features/autocorrect)

### Dynamic Macros

Record and replay macros at runtime. Not persistent across reboots. Useful for repetitive editing tasks.

```c
// Assign to keys
DM_REC1   // start recording macro 1
DM_RSTP   // stop recording
DM_PLY1   // play macro 1
```

[Documentation](https://docs.qmk.fm/features/dynamic_macros)

### Leader Key (modernized)

Press a leader key, then a sequence of keys to trigger an action. Like Vim's leader key. API completely rewritten in 2023.

```c
void leader_end_user(void) {
    if (leader_sequence_two_keys(KC_D, KC_D)) {
        // Leader + D + D: delete line
        SEND_STRING(SS_TAP(X_HOME) SS_LSFT(SS_TAP(X_END)) SS_TAP(X_BSPC));
    }
}
```

[Documentation](https://docs.qmk.fm/features/leader_key)

## Nice to Have

### One Shot Keys

Modifier stays active for exactly one keypress. Tap Shift, then tap a letter -- no holding required. Useful for one-handed operation.

```c
OSM(MOD_LSFT)  // one shot left shift
OSL(layer)      // one shot layer
```

[Documentation](https://docs.qmk.fm/one_shot_keys)

### Speculative Hold

Makes mod-taps feel instant by applying the modifier immediately on keydown. If tapped, the speculative modifier is cancelled before the tapping keycode is sent. Useful for Shift+Click.

[Documentation](https://docs.qmk.fm/tap_hold)

### Mouse Keys Improvements

Multiple acceleration modes: kinetic (quadratic curve), inertia, constant, combined. The MOUSE layer could feel much better with kinetic mode.

[Documentation](https://docs.qmk.fm/features/mouse_keys)

### Community Modules (2025)

Third-party code modules importable into QMK builds. Hooks for init, key processing, suspend, and shutdown. The `zsa/defaults` module already in use is built on this framework.

[Documentation](https://docs.qmk.fm/features/community_modules)

### Send String Improvements

New delay functions for ARM devices and inline delays within macros.

```c
SEND_STRING("hello" SS_DELAY(100) " world");  // 100ms pause mid-string
send_string_with_delay("hello", 50);           // 50ms between each character
```

### Unicode String Support

Direct Unicode output, including emoji.

```c
send_unicode_string("<<>>");  // sends actual Unicode characters
```

## Summary: Best Upgrades for This Keymap

| Feature | Why | Effort |
|---|---|---|
| **Chordal Hold** | Home row mods (`CTL_T`, `SFT_T`, `ALT_T`) become much more reliable | Low -- add to rules.mk |
| **OS Detection** | Auto-switch Mac/PC shortcuts instead of manual defines | Medium -- refactor process_record_user |
| **Caps Word** | Auto-disabling caps lock, assign to one key | Low -- add one key |
| **Repeat Key** | Doubled French letters (ll, ss, tt) with one key | Low -- add one key |
| **Key Overrides** | Simplify custom shift behavior | Medium -- replace some process_record_user cases |
| **Combos** | Two-key shortcuts with zero RAM cost | Medium -- define combos |
