# Scarab Coil — marble shooter prototype

A Zuma-style marble shooter prototype in a single HTML file (no build step, no libraries).

## Play it
Open `index.html` in any browser, including Chrome on Android.

- Aim with the mouse or your finger, release to shoot.
- Tap the scarab (or right-click / press Space) to swap the current and next marble.
- Groups of 3+ of the same colour pop. If the marbles on both sides of the gap
  match, the front of the chain slides back and can set off a combo.
- Clear the chain before it reaches the hole.

## How it works (in `index.html`)
- **Track:** an entry channel plus a spiral, resampled into a lookup table with one
  point per pixel of length, so `at(s)` turns "distance along the track" into x/y.
- **Chain:** an array of marbles, each storing only its colour and distance `s`.
  Only the last marble is pushed; any marble it touches is pushed along with it,
  so gaps stay open until the back of the chain catches up.
- **Insertion:** a shot marble that hits the chain is inserted in front of or behind
  the marble it hit, then neighbours are pushed apart and matches are checked.
- **Retraction/combos:** a front segment slides back when the colours on both
  sides of its gap match; hitting the back segment re-checks for a match and
  raises the combo multiplier.
- **Levels:** longer, faster chains and a 5th colour from level 3 (`levelCfg`).

## Next steps
- Tune difficulty (speed, colours, chain length) with playtesters.
- Add more track shapes, sound, power-ups.
- Package for Google Play: wrap it with Capacitor, or port the logic to Godot.
