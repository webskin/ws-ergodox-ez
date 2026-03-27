# Layers (14 total)

## Base Layers

| Layer | Description |
|---|---|
| **BEPO** | Bepo French ergonomic layout -- primary typing layer |
| **AZERT** | AZERTY French layout -- alternative, toggled via `DF()` |

## Symbol & Modifier Layers

Paired for Bepo and AZERTY:

| Bepo | AZERTY | Side | Content |
|---|---|---|---|
| **MISCL1** | **MISCL1AZ** | Left | Programming symbols: arrows (`->` `=>` `~>` `|>`), operators, math |
| **MISCL2** | **MISCL2AZ** | Left | Brackets & parens: `() [] {} <> <<>>` |
| **MISCR1** | **MISCR1AZ** | Right | Navigation: arrows, Home/End, PgUp/PgDn, volume |
| **MISCR2** | **MISCR2AZ** | Right | Selection: Shift+navigation, undo/redo |

## Specialized Layers

| Layer | Description |
|---|---|
| **NUMPAD** | Numeric keypad + F1-F12 function keys |
| **MOUSE** | Mouse movement, clicks, scroll wheel |
| **FXXNPOH** | One-handed F-keys and numpad (left hand) |
| **GAME1** | Gaming-optimized layout |

## LED Layer Indicators

The three right-side status LEDs show the active layer:

| LED 1 | LED 2 | LED 3 | Layer |
|---|---|---|---|
| ON | | | MISCL1 / MISCL1AZ |
| | ON | | MISCL2 / MISCL2AZ |
| | | ON | MISCR1 / MISCR1AZ |
| ON | ON | | MISCR2 / MISCR2AZ |
| ON | | ON | NUMPAD |
| | ON | ON | MOUSE |

## RGB Underglow (Shine only)

Wrapped in `#ifdef RGBLIGHT_ENABLE` for Base compatibility:

| Layer | Color |
|---|---|
| BEPO | Off (black) |
| AZERTY | Green |
| FXXNPOH | Red |
| GAME1 | Magenta |
