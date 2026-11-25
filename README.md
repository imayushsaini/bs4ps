# BombSquad (Ballistica) - PlayStation 4 Homebrew Port

[![Platform: PS4](https://img.shields.io/badge/Platform-PlayStation%204-003791?style=flat&logo=playstation)](https://github.com/imayushsaini/bs4ps)
[![Toolchain: OpenOrbis](https://img.shields.io/badge/Toolchain-OpenOrbis-blueviolet?style=flat)](https://github.com/OpenOrbis/OpenOrbis-PS4-Toolchain)
[![Target: GoldHEN](https://img.shields.io/badge/Environment-GoldHEN-gold?style=flat)](https://github.com/SiSTR0/GoldHEN)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status: Playable](https://img.shields.io/badge/Status-60FPS%20Playable-success)](https://github.com/imayushsaini/bs4ps)

An unofficial, open-source homebrew port of **BombSquad** (powered by the **Ballistica** engine) for jailbroken PlayStation 4 consoles.

This port runs natively on the PS4 hardware using the open-source **OpenOrbis PS4 Toolchain**, featuring hardware-accelerated OpenGL ES rendering (via Piglet), full DualShock 4 rumble/vibration, local multiplayer for up to 8 players, and persistent hardware texture caching.

---

## 🎮 Features

- **Smooth 60 FPS Gameplay:** Hardware-accelerated graphics using PS4's Piglet GLES2 stack.
- **Full DualShock 4 Support:** Native controller input mapping with haptic vibration / rumble support.
- **Local Multiplayer:** Connect multiple DualShock 4 controllers on the same console for party battles.
- **Persistent Texture Cache:** High-resolution textures are decompressed and cached to internal storage on first launch for fast subsequent boot times.
- **Pre-compiled Python Bytecode:** Integrated embedded CPython 3.14 with pre-compiled `.pyc` bytecode.
- **Complete Sound & Music Support:** Multi-channel 3D positional audio.

---

## 📋 Requirements & Prerequisites

To run this homebrew on your PlayStation 4, you will need:

1. **Jailbroken PS4 Console** running **GoldHEN** (tested and verified on PS4 firmware up to **13.52** / **11.00**).
2. **PS4-Xplorer** or an active **FTP client** (e.g., FileZilla) connected to your PS4.
3. **Required System Shaders & GLES Libraries (`.sprx`):**  
   The port links against Piglet and Shader Compiler runtime modules. Ensure the following two files exist on your PS4's internal storage:
   - `/data/self/system/common/lib/libScePigletv2VSH.sprx`
   - `/data/self/system/common/lib/libSceShaccVSH.sprx`

> [!IMPORTANT]
> If these `.sprx` libraries are missing from `/data/self/system/common/lib/`, the game will fail to launch or crash back to the PlayStation home menu. Most homebrew GLES games require these same two files. You can copy them to `/data/self/system/common/lib/` using PS4-Xplorer or GoldHEN FTP.

---

## 🚀 Installation Guide

### Step 1: Place Required SPRX Libraries
1. Open **PS4-Xplorer** or connect to your console via **GoldHEN FTP** (IP: console IP, Port: `2121` or `1337`).
2. Navigate to the directory:
   ```text
   /data/self/system/common/lib/
   ```
   *(Create the subdirectories if they do not already exist).*
3. Copy both `libScePigletv2VSH.sprx` and `libSceShaccVSH.sprx` into that directory.

### Step 2: Install the Game Package (PKG)
1. Download the latest **`IV0000-BOMB00001_00-BALLISTICAPS4000.pkg`** from the [Releases](https://github.com/imayushsaini/bs4ps/releases) page.
2. Copy the `.pkg` file to the root of an exFAT/FAT32 USB drive or transfer it to `/data/pkg/` on the PS4.
3. On your PS4, go to **Settings** -> **GoldHEN** -> **Package Installer**.
4. Select and install the package.
5. Launch **BombSquad** from the PlayStation home screen!

---

## ⏱️ Important Note on First Launch & Texture Caching

- **First Launch Takes Longer (1–2 minutes):**  
  On the very first launch, the game performs initial filesystem setup and decompresses ~210 high-resolution textures, converting them into optimized `.batc` format saved to your PS4's internal HDD (`/data/ballistica/cache/textures/`).
- **Subsequent Launches (Fast):**  
  Once cached, all future game boots hit the cache instantly and load in seconds!
- **Black Screen During Boot:**  
  While assets are initializing on boot, the screen remains black before showing the main menu. Please do not close the game; allow the initial loading sequence to finish.

---

## 📂 File Locations & Troubleshooting

All user configurations, save files, cache, and logs are kept isolated in `/data/`:

| Path | Description |
| :--- | :--- |
| `/data/ballistica/config.json` | Game settings, input configurations, audio volumes, and profiles. |
| `/data/ballistica/cache/textures/` | Persistent decompressed texture cache (`.batc` files). |
| `/data/ballistica/cache/` | General game cache and runtime data. |
| `/data/ballistica_debug.log` | Engine diagnostic and debug log output. |

### How to Reset / Fix Issues:
If you ever experience corrupted settings, graphics glitches, or want a completely fresh start:
1. Open **PS4-Xplorer** or your FTP client.
2. Delete the folder:
   ```text
   /data/ballistica/
   ```
3. Restart the game. It will automatically regenerate a fresh configuration and rebuild the texture cache on next launch.

---

## 🕹️ Controls (DualShock 4)

| Button | Action |
| :--- | :--- |
| **Left Stick / D-Pad** | Move Character / Navigate Menus |
| **Cross (✕)** | Punch / Confirm Menu Item |
| **Circle (◯)** | Drop Bomb / Cancel & Back |
| **Square (▢)** | Jump |
| **Triangle (△)** | Pick Up / Throw Objects & Opponents |
| **L1 / R1 / L2 / R2** | Triggers (configurable in Game Settings) |
| **Options** | Pause / Main Menu |
| **Touchpad** | Menu Navigation / Select |

*Custom button mappings and sensitivity can also be configured inside the in-game Settings menu.*

---

## 🤝 Credits & Acknowledgments

- **Original Game & Engine:**  
  Huge thanks and credits to **Eric Froemling** ([@efroemling](https://github.com/efroemling)) for creating [BombSquad](https://www.froemling.net/apps/bombsquad) and open-sourcing the [Ballistica](https://github.com/efroemling/ballistica) engine.
- **PlayStation 4 Port:**  
  Ported by **Ayush Saini** ([@imayushsaini](https://github.com/imayushsaini)) — architecture porting, OpenOrbis toolchain integration, DualShock 4 controls, and texture caching pipeline.
- **Homebrew Ecosystem:**  
  - **OpenOrbis Team** for the open-source [OpenOrbis PS4 Toolchain](https://github.com/OpenOrbis/OpenOrbis-PS4-Toolchain).
  - **SiSTRo** and the GoldHEN development team.
  - The PlayStation 4 homebrew development community.

---

## ⚖️ Disclaimer & Legal Notice

This project is an unofficial, non-commercial community homebrew port intended solely for personal, educational, and homebrew entertainment on jailbroken PlayStation 4 consoles.

- This project is **not** affiliated with, authorized, or endorsed by Sony Interactive Entertainment Inc.
- All code contributed for the PS4 port is released under the [MIT License](LICENSE).
- BombSquad and Ballistica game code are licensed under the MIT License by Eric Froemling. Game assets remain the property of their respective creator. If you enjoy the game, please support the official release on official supported platforms at [froemling.net](https://www.froemling.net/apps/bombsquad).
