# Molecoil — molecular marble shooter prototype (working title)

A rogue polymer is crawling toward the nuclear pore. Fire atoms into the chain and match
3 or more of one element to break it apart. One HTML file, no build step, no libraries.

## Play it
Open `index.html` in any browser, including Chrome on Android. Built phone-first: the
board fills a portrait screen and adapts to the phone's shape.

- Touch and hold to aim (the guide line shows which atom you will hit), release to fire.
- Tap the nucleus (or right-click / press Space) to swap the loaded and next atom.
- Pause button (or P / Esc); the game also pauses when you leave the app.
- **Atoms** are elements — O, S, Cl, N, K — coloured after the chemists' CPK convention
  where possible, with the symbol printed on each one.
- **Chain reactions:** when the atoms on both sides of a gap match, the front of the chain
  slides back and can pop again, raising the combo multiplier.
- **Power atoms** (glowing): Freeze, Reverse reaction, Fission.
- **Streaks:** consecutive hits add a bonus; a miss resets it.
- **Mutations** strike mid-level, each announced first and shown with a timer:
  Chirality Flip (aim mirrored), Quantum Tunnelling (shots pass through faded atoms),
  Transmutation (two elements swap; new runs pop), Mitosis (shots divide in two).
  Harmful ones show a "Repair · watch ad" button — a placeholder for a rewarded ad.
- **Level select:** 10 demo levels, all unlocked, with track previews and saved stars
  (1–3 per level, by how close the chain got to the pore).
- **Ten tracks in five worlds** (Cytoplasm, Chlorophyll, Neuron, Blood, Plankton):
  Helix, Villi, Synapse, Beta Sheet, Hairpins, Cilia, Membrane, Osmosis, Trefoil,
  Supercoil. Where a track passes back over itself, the lower strand runs through a
  membrane channel; atoms fade into it (never cut in half) and can't be hit inside.
- Synthesised sound, vibration on Android, a heartbeat warning near the pore.

## How it works (in `index.html`)
- **Track:** each track is a list of points (built with formulas or the `pen` helper:
  `fwd`, `arc`), resampled into one point per pixel of length so `at(s)` turns
  "distance along the track" into x/y.
- **Crossings:** `buildPath` finds them automatically — any point closer than a groove
  width to a part of the track at least 100px earlier becomes a tunnel. Channels,
  bridges and mouths are drawn on a layer under the atoms; atoms fade near tunnels.
- **Chain:** only the last atom is pushed; atoms it touches are pushed along, so gaps
  stay open until the back catches up. Each gap remembers the combo level that opened it.
- **Levels:** `levelCfg` (chain length, speed, colours, track, world). Chain speed is
  scaled by track length so short tracks stay fair.

## Next steps
- Playtest and tune difficulty; add sound assets and a level map.
- Package for Google Play (Capacitor, or port to Godot) and hook the ad button to AdMob.
- Before launch: trademark search on the final name.
