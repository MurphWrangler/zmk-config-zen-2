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
- Base-layer vertical combos: Q+A = Escape; W+R = Tab; J+M = Menu. These are initial choices, not previously finalized. Press together within 50 ms after at least 150 ms without another keypress.
- All sticky modifiers use quick release and a 300 ms timeout.
- Shift tap dance/Caps Word removed. GUI remains in the original index-finger positions.
- All 30 finger bindings per layer remain as in the source, except sticky modifiers share the new behavior and the former Studio unlock key enters the bootloader.
- Layer-taps use balanced 200 ms timing. Space/Enter allow a held repeat after a second tap within 125 ms. Alt tap arms sticky Alt for the next key; holding it selects Number.
- RGB is disabled; sleep after 15 minutes.

## Misc layer

Top-left five keys select Bluetooth profiles 1–5. Bottom-left key clears only the current profile; the next key toggles USB/Bluetooth output. Left bottom inner-index key (the base V position) enters the bootloader. Use profile clearing only when you intend to re-pair that profile.

## Flash

Connect one keyboard with a data-capable USB cable. Double-tap its reset button to enter the UF2 bootloader; copy `re-gret-forrest.uf2` onto the drive. It will reboot automatically. Repeat for the second keyboard. Do not disconnect during the copy. Select a Bluetooth profile and pair each keyboard separately.

Build success verifies compilation, not physical key scanning, Bluetooth behavior, combo ergonomics or the previously observed repeat issues. Test one keyboard first: every base key, all four thumbs, number/symbol/navigation/function/misc layers, modifier chords, held minus, repeated shifted letters, output switching and Bluetooth pairing.

ZMK and the manufacturer's keyboard module are pinned to exact commits in `config/west.yml` for reproducible builds.
