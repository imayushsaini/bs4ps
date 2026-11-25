# Changelog

All notable changes to the BombSquad (Ballistica) PlayStation 4 port will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-11-25

### Added
- **First Version Release:** Initial port of BombSquad running the **1.8.10** build (build 23095) natively on jailbroken PlayStation 4 consoles.
- **60 FPS Performance:** Stable 60 FPS gameplay using PS4 Piglet OpenGL ES 2.0 hardware acceleration.
- **Working Co-op & Local Multiplayer:** Full support for local multiplayer and co-op campaigns with multiple DualShock 4 controllers connected to the same console.
- **DualShock 4 Controller Support & Rumble:** Full native gamepad controls, button mappings, and working joystick rumble / vibration haptics.
- **Audio System:** Fully functional positional 3D sound effects and in-game music tracks.
- **Persistent Texture Caching:** Custom texture decompression pipeline saving optimized `.batc` textures to internal storage (`/data/ballistica/cache/textures/`) for fast subsequent loads.
- **Custom Data Directory:** User configuration, saves, caches, and logs routed cleanly to `/data/ballistica/`.

### Known Issues
- Long boot time accompanied by a black screen during initial startup while assets initialize (work in progress to optimize startup times; does not impact gameplay).
- Online play and network matchmaking are currently not enabled.
- Local multiplayer with multiple joysticks is working, but LAN play with nearby devices is not working.
