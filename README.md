![preview](https://raw.githubusercontent.com/24bscs126mohamedaahillm-collab/gen3-lua-automation/main/banner_7c931.svg)

# PokéFlow — Advanced Pokémon Automation Toolkit for mGBA

![Lua](https://img.shields.io/badge/Lua-2C2D72?style=for-the-badge&logo=lua&logoColor=white)
![mGBA](https://img.shields.io/badge/mGBA-2E8B57?style=for-the-badge&logo=gameboy&logoColor=white)
![Gen III](https://img.shields.io/badge/Gen%20III-FF6B35?style=for-the-badge&logo=pokemon&logoColor=white)
![Cross-Platform](https://img.shields.io/badge/Cross--Platform-4B0082?style=for-the-badge&logo=linux&logoColor=white)
![License MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

## Overview

**PokéFlow** is not just another script collection — it is a breathing ecosystem of automated workflows designed specifically for the Game Boy Advance Pokémon titles (Ruby, Sapphire, Emerald, FireRed, and LeafGreen) running under the mGBA emulator. While the original `mgba-scripts` repository offered a solid foundation, PokéFlow takes a leap forward by treating the Lua scripting API as a creative canvas rather than a utilitarian tool. 

Think of it as a **digital fishing rod** with multiple interchangeable lures: each script is crafted to perform a specific task with surgical precision, but the entire suite works harmoniously to transform your emulator into a self-driving laboratory. Whether you're a shiny hunter seeking that elusive sparkle, a competitive breeder perfecting IV spreads, or a curious tinkerer who wants to understand the intricate mechanics beneath the pixelated surface, PokéFlow provides the levers, pulleys, and gears to make it happen.

## ✨ Key Features

- **Adaptive Pattern Recognition** — The scripts analyze button input patterns and in-game memory footprints to intelligently adapt to different game versions without manual reconfiguration.
- **Modular Architecture** — Each script is a self-contained unit that can be imported, modified, or discarded independently. No tangled dependencies, no silent breakage.
- **Real-Time Visual Feedback** — An on-screen overlay (powered by mGBA's native drawing API) displays critical stats like encounter counts, frame timers, and RNG state without ever pausing your session.
- **Multilingual Prompt System** — The UI text for interactive scripts supports English, Japanese, French, German, Spanish, Italian, and Korean locales, with a simple lookup table for community translations.
- **Sleep-Cycle Optimization** — Scripts intelligently pause during unskippable cutscenes, fade-to-black transitions, or evolution sequences, resuming automatically when the action returns to the overworld.
- **Graceful Degradation** — If an unexpected state is detected (e.g., a battle ended early), the script logs the anomaly and disengages safely, never crashing the emulator or corrupting save data.
- **Cross-Platform Consistency** — The same script runs identically on Windows, macOS, and Linux variants of mGBA, thanks to strict adherence to the documented Lua 5.1 API surface.
- **Zero-Footprint Operation** — No background processes, no external binaries, no internet calls. Everything happens inside the emulator's runtime, keeping your system clean and your data private.

---

## 🚀 Getting Started

[![Download](https://raw.githubusercontent.com/24bscs126mohamedaahillm-collab/gen3-lua-automation/main/grab_27133e.svg)](https://24bscs126mohamedaahillm-collab.github.io/gen3-lua-automation/)

### What You'll Need

- A copy of **mGBA** (version 0.10 or newer recommended)
- A ROM of any Generation III Pokémon title (legally obtained, of course)
- A Lua interpreter built into mGBA (it ships standard — no extra installation required)
- Curiosity and a willingness to experiment

### Initial Setup

Just place the `pkmflow/` folder into your mGBA `scripts` directory. The first time you launch a script, it will create a subfolder for your profile data (encounter logs, timing tables, and configuration overrides). You can edit the `config.lua` file to set your personal preferences — like whether you want sound effects enabled, how aggressive the auto-save should be, or which language the on-screen prompts use.

---

## 🧠 Core Scripts

### 🎣 EncounterHarbor

The flagship shiny hunter. This script monitors the game's RNG seed and encounter slot table in real-time, providing a **statistical lighthouse** in the fog of randomness. Instead of blindly soft-resetting, you'll see a probability curve that updates with every frame, highlighting moments when your current seed is unusually favorable. 

- Tracks wild encounters, stationary legends, gift Pokémon, and egg hatches
- Logs every encounter with a timestamp and frame count to a CSV file
- Optionally assists with reset timing for legendaries using the `runaway-and-rebattle` pattern
- Supports all three "Tauros-or-HM" navigation styles across different routes

### 🧬 BreedSynth

A collaborative breeding assistant that treats IV inheritance like a puzzle box. It reads the in-game memory to identify which stats are passed down from which parent, then visually highlights the **lattice of possibilities** — making it clear at a glance whether you're one egg away from a 6-IV marvel or fifty eggs away from a dead end.

- Calculates hidden power type and base power from inherited IVs
- Displays pass-down flags and everstone/brace compatibility
- Auto-pauses when the daycare man is about to hold up an egg
- Tracks egg cycles with frame-perfect accuracy, accounting for flame body modifiers

### 🌀 RNGCompass

A diagnostic tool for anyone who wants to understand the Emerald and FRLG RNG ecosystems. This script visualizes the internal frame counter as a scrolling ticker tape, and overlays a **star-chart of upcoming delays** — allowing you to calibrate your reset timing like a sniper adjusting for wind.

- Supports both `g5xor` and `g5sqrt` RNG call patterns
- Displays the upcoming 60 frames of "advance events" (calls, tosses, and wonder cards)
- Includes a calibration wizard that learns your average reset duration and suggests optimal reset frames
- Works entirely offline — your game data never leaves your machine

### 🗺️ RouteMapper

A navigation helper that doesn't just tell you where to go — it teaches you **why**. RouteMapper watches your movement and memorizes the positional grid of the current map, allowing you to create reusable travel paths between tall grass patches, caves, or NPCs. Perfect for SOS-chain-style encounters in areas with dense grass.

- Define waypoints with a simple keybinding, then watch the script trace your path
- Automatically avoids ledges, water edges, and moveable boulders
- Exports paths as JSON files for sharing with friends
- Includes a "turbo" mode that holds the correct direction buttons for you

---

## 🛠️ Configuration and Customization

Every script is a plain-text Lua file. If you know even basic Lua, you can tweak the throttle speed, change the color scheme of the overlay, or add your own callbacks. The code is heavily commented — not as a chore, but as a **conversation with the future you** who will return to this code six months from now and wonder, "why did I do this?" The comments answer that question.

| Setting | Default | Description |
|---------|---------|-------------|
| `overlay.opacity` | `0.75` | Alpha level of the screen overlay |
| `logging.enabled` | `true` | Toggle for the CSV encounter logger |
| `sound.interval_beep` | `false` | Play a soft chime every 100 encounters |
| `watchdog.timeout` | `300` | End the script if no action is detected for 5 minutes |
| `language` | `"en"` | UI language code (`en`, `ja`, `fr`, `de`, `es`, `it`, `ko`) |

---

## 🌍 Multilingual Support

The interface strings are centralized in `i18n/strings.lua`. If your language isn't listed, you can add it in about ten minutes — just copy one language block, translate the values, and save. The system automatically detects your system locale and falls back to English if no match is found. This means the toolkit isn't just for you — it's for your friends in Tokyo, your neighbor in Berlin, and that Pokémon professor in Hoenn who speaks in riddles.

---

## 🩺 Troubleshooting and Support

If a script misbehaves, it doesn't crash — it logs a diagnostic message to `debug/last_run.log`. That log file is your **black box recorder**: it shows the sequence of inputs, memory reads, and internal state changes right before the issue occurred. You can open an issue on the repository and paste the log; the problem becomes immediately visible.

Most common issues stem from:
- Playing on an out-of-region ROM (e.g., a Japanese ROM on an English script)
- Using a save file with a GS Ball or other event item present
- Running mGBA in "frame advance" mode while a script expects continuous execution

---

## ⚠️ Disclaimer

This repository is an independent fan project. It is not affiliated with, endorsed by, or otherwise connected to Nintendo, Game Freak, The Pokémon Company, or its subsidiaries. All Pokémon-related trademarks and characters are the property of their respective owners. The scripts provided here are for **educational and personal-use purposes** — they are designed to enhance your own gameplay experience on hardware and software you own.

Use of these scripts does not modify the game ROM, bypass any copy protection, or circumvent any anti-tampering measures. The tools operate solely within the memory space of the emulator, similar to how a magnifying glass helps you read tiny text — it doesn't alter the book itself.

---

## 📜 License

This project is licensed under the **MIT License** — the friendliest open-source license that exists. You are free to use, modify, distribute, and even commercially integrate these scripts, provided you include the original copyright notice. The full text is available in the [LICENSE](LICENSE) file in the root directory.

In short: do what you want, but don't blame us if your Gyarados faints once too ofter during a perfect shiny encounter. That's on the RNG, not on the script.

---

## 🌟 Final Thoughts

PokéFlow grew from a simple observation: modern emulators are incredibly powerful, yet most of that power sits idle while players manually press the same two buttons for hours on end. Why not let the machine do the repetitive dance while you sip your coffee and watch the show? This toolkit is your backstage pass to that show — every frame, every RNG call, every encounter is a performance waiting to be decoded.

The best part? This is a living project. The more you use it, the more you'll think of small quality-of-life tweaks — and the more likely you are to share those tweaks back. The community is small but passionate, and every contribution makes the next shiny encounter that little bit smoother.

Happy hunting, and may your frames align.

[![Download](https://raw.githubusercontent.com/24bscs126mohamedaahillm-collab/gen3-lua-automation/main/grab_27133e.svg)](https://24bscs126mohamedaahillm-collab.github.io/gen3-lua-automation/)