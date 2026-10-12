# Base Probability Scanner (Fabric 1.21.1)

A client-side heuristic scanner prototype that draws colored wireframe boxes around suspicious loaded chunks.

## Features
- Red / yellow / green region outlines based on heuristic score.
- Scans nearby loaded chunks around the player.
- Scores clusters of utility/crafted-looking blocks, unusual growth blocks, water edges, and relatively flat surface terrain.
- Tracks a simple per-chunk growth signature between scans during the current session.

## Important limitations
- This is a heuristic prototype, not a true probability model.
- Minecraft does not expose a reliable universal flag that says whether a block was crafted or player-placed. The scanner only recognizes block types commonly associated with player activity.
- The growth signature is a rough observation-based signal, not a verified growth history. It can change because the scanned area or visible block states change.
- The scan only sees client-loaded world data. It cannot inspect unloaded chunks or recover historical changes from before the mod was running.
- No chat commands or config screen are included yet. Tune `minimumScore`, `SCAN_RADIUS_CHUNKS`, and `SCAN_INTERVAL_TICKS` in `BaseProbabilityScannerClient.java`.

## Build
Requires Java 21 and Gradle.

From this directory:
```bash
gradle build
```
The compiled mod should appear in `build/libs/`.

## Install
1. Install Fabric Loader for Minecraft Java 1.21.1.
2. Install Fabric API for Minecraft 1.21.1.
3. Build the project, then copy the produced `base-probability-scanner-1.0.0.jar` into `.minecraft/mods`.
4. Launch the Fabric 1.21.1 profile.

This is a source project, not a precompiled jar. Rendering and mapping APIs can change between Minecraft versions.
