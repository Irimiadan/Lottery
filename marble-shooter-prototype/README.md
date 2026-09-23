# Cozy Cure — a cozy virus-busting shooter (working title)

A chain of grumpy viruses is creeping toward your patient's heart. Send out friendly
immune cells and match 3 or more of the same strain to wipe them out. If the virus
reaches the heart, the monitor flatlines — and the patient gets another try.
One HTML file, no build step, no libraries.

## Play it
Open `index.html` in any browser, including Chrome on Android. Built phone-first.

- Touch and hold to aim (the guide line shows which virus you will hit), release to fire.
- Tap the white blood cell (or right-click / press Space) to swap your immune cell.
- **Five strains**, each with its own colour and spike shape (knobs, spikes, squares,
  crowns, petals), so they're easy to tell apart for colour-blind players.
- **Heart monitor** at the top: the heart rate climbs as the virus gets closer, the heart
  at the end of the track beats along, and it flatlines if the virus gets in.
- **Chain reactions**, **streaks**, **medicine power-ups** (Ice pack, Antiviral, Vaccine).
- **Mutations** mid-level: Dizzy Fever (aim mirrored), Stealth Strain (shots pass through
  hidden viruses), Mutation (two strains swap), Booster Shot (shots double). Harmful ones
  show a "Cure · watch ad" placeholder button.
- **Ten body levels** in five warm worlds (Blush, Peach, Honey, Berry, Cocoa): Bloodstream,
  Intestine, Nerve, Ribs, Lymph Nodes, Airways, Stomach, Kidney, Heart Valves, Brain.
- **Sound:** a soft, warm low-passed mix — marimba-like pops, a heartbeat when the virus
  is close — and a slow cosy music loop (pad chords, round bass, music-box melody), all
  generated in code. Separate music and sound buttons.

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
