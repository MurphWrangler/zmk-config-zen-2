# Re-Gret firmware

Port of the Colemak config from `MurphWrangler/zmk-config-zen-2`, branch `studio`, commit `e04745c36a6736ab45a73b1a3202a2eb450a563a`.

One identical UF2 is intended for both assembled wireless Re-Grets (Seeed XIAO nRF52840). Each keyboard retains its own Bluetooth pairings.

## Controls

| Left-to-right thumb | Tap | Hold |
| --- | --- | --- |
| Left outer | Sticky Alt | Number |
| Left inner | Sticky Shift | Shift |
| Right inner | Space | Navigation |
| Right outer | Enter | Symbol |

- Number + Navigation activates Function. Hold left outer Alt/Num and right inner Space/Nav for F1–F12. Navigation + Symbol no longer activates Function.
- Number + Symbol activates Misc. Hold left outer and right outer thumbs.
- Base-layer vertical combos: F+S = Escape; T+D = Tab; J+M = Menu. Press together within 50 ms after at least 150 ms without another keypress.
- All sticky modifiers use quick release, ignore other modifiers for chaining, and have a 300 ms timeout.
- Shift tap dance/Caps Word removed. GUI remains in the original index-finger positions.
- Assigned keys preserve the discussed layout. Unused finger positions on Number, Function and Misc are explicit no-ops; Navigation keeps intentional transparent letters for shortcuts.
- Layer-taps use balanced 200 ms timing. Space/Enter allow a held repeat after a second tap within 125 ms. Alt tap arms sticky Alt for the next key; holding it selects Number.
- RGB is disabled; sleep after 15 minutes.

## Layer cleanup and binding audit

Symbol is the discussed punctuation layout. Parentheses are adjacent on the left home row; curly braces are directly below square brackets. Apostrophe is on base, and Shift+apostrophe produces double quote. Shift+base slash produces question mark; comma, period and slash remain on base. The Symbol layer now includes backtick and backslash and has no duplicate right brace.

| Row | Left five keys | Right five keys |
| --- | --- | --- |
| Symbol top | `! @ # $ %` | `^ & * + =` |
| Symbol home | Backtick, `[`, `]`, `(`, `)` | Backslash, GUI, Ctrl, Alt, Shift |
| Symbol bottom | `~ { } < >` | Pipe, `-`, `_`, `:`, `;` |
| Number top | Esc, Backspace, Delete, `=`, Num Lock | Divide, 7, 8, 9, Multiply |
| Number home | Shift, Alt, Ctrl, GUI, Right Alt | Subtract, 4, 5, 6, Add |
| Number bottom | Unused (no action) | 0, 1, 2, 3, Decimal |
| Navigation top | Esc, Home, Up, End, Page Up | Tab, Menu, Enter, unused, unused |
| Navigation home | Base A, Left, Down, Right, Page Down | Base M, GUI, Ctrl, Alt, Shift |
| Navigation bottom | Base Z, X, C, D, V | Base K, Backspace, Delete, Print Screen, Insert |

Number uses true keypad digits and operators, including decimal. Turn Num Lock on for numeric entry; the key at base B toggles it while holding Number. Top-left W/F positions give Backspace/Delete without releasing Number.

Navigation removes prebound Select All/Undo/Cut/Copy/Paste/Paste Special and duplicate punctuation. Use the sticky Ctrl/Alt modifiers with base letters instead; those letter positions remain transparent on Navigation. There is no dedicated Caps Lock, media Stop, Pause/Break, Scroll Lock or mouse layer; these were not required by the discussed layout. Shift is a sticky/held modifier, with no Caps Word or tap dance.

Audited: all 26 letters; digits 0–9 and decimal; US punctuation; Space/Enter/Escape/Tab/Menu; Backspace/Delete/Insert; arrows/Home/End/Page Up/Page Down; Shift/Ctrl/Alt/GUI/Right Alt; F1–F12; media previous/play-pause/next, mute/volume, brightness; Print Screen; five Bluetooth profiles, current-profile clear, output toggle and bootloader. Every layer has 34 bindings; every layer has an access path. Firmware compilation and UF2 validation do not verify physical ergonomics or held-key behavior.

## Transparency policy

Number has five blank left-bottom positions. Function has five blank positions (base apostrophe, O, C, V and slash); they no longer inherit navigation actions or letters. Misc has five blank left-home positions, two blank left-bottom positions (base C and D), and all 15 right-hand finger positions blank. Symbol has no unused finger positions. Navigation retains its base letters for modifier shortcuts. All four thumbs remain transparent on every upper layer so the base tap/hold behaviors and cross-hand layer chords remain accessible.

## Misc layer

The right-hand finger positions are all no-ops; the thumb keys retain their base behaviors. Top-left five keys select Bluetooth profiles 1–5. Bottom-left key clears only the current profile; the next key toggles USB/Bluetooth output. Left bottom inner-index key (the base V position) enters the bootloader. Use profile clearing only when you intend to re-pair that profile.

## Flash

Connect one keyboard with a data-capable USB cable. Double-tap its reset button to enter the UF2 bootloader; copy `re-gret-forrest.uf2` onto the drive. It will reboot automatically. Repeat for the second keyboard. Do not disconnect during the copy. Select a Bluetooth profile and pair each keyboard separately.

Build success verifies compilation, not physical key scanning, Bluetooth behavior, combo ergonomics or the previously observed repeat issues. Test one keyboard first: every base key, all four thumbs, number/symbol/navigation/function/misc layers, modifier chords, held minus, repeated shifted letters, output switching and Bluetooth pairing.

ZMK and the manufacturer's keyboard module are pinned to exact commits in `config/west.yml` for reproducible builds.
