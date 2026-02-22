# nevercorne — Corne ZMK config

[![Build](https://github.com/neversad-dev/zmk-config/actions/workflows/build.yml/badge.svg)](https://github.com/neversad-dev/zmk-config/actions/workflows/build.yml)
[![Release](https://github.com/neversad-dev/zmk-config/actions/workflows/release.yml/badge.svg)](https://github.com/neversad-dev/zmk-config/actions/workflows/release.yml)
[![ZMK v0.3.0](https://img.shields.io/badge/ZMK-v0.3.0-blue)](https://github.com/zmkfirmware/zmk)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

ZMK-based firmware for a **Corne LP** (low-profile split 40% keyboard). Built with [ZMK](https://zmk.dev/).

---

## Hardware (Corne Cherry v3)

| Component | Link |
|-----------|------|
| Corne LP V3 PCB Black | [boardsource](https://www.boardsource.xyz/products/Corne_LP) |
| nice!nano v2.0 | [Nice Keyboards](https://nicekeyboards.com/docs/nice-nano/) |
| Choc Hot Swap Sockets | [boardsource](https://www.boardsource.xyz/products/Choc_Hot_Swap_Sockets) |
| Choc Purpz / Choc Robin switches | [boardsource](https://www.boardsource.xyz/store/5ef6f7376786dc1e65a80744) / [Amazon](https://www.amazon.com/Profile-Mechanical-Switch-Keyboard-Switches/dp/B0CKGLZ3BW) |
| MBK blanks keycaps | [boardsource](https://www.boardsource.xyz/products/MBK_blanks) |
| Case | Space Grey Aluminum Corne LP Case |

---

## Build & release

- **CI builds** (on every push/PR): [Actions](https://github.com/neversad-dev/zmk-config/actions) → select a run → **Artifacts** → download the firmware.
- **Releases** (on version tags): Push a tag (e.g. `v0.0.2` or `v1.0.0+zmk0.3.0`) to trigger the release workflow. Firmware is attached to the [Releases](https://github.com/neversad-dev/zmk-config/releases) page.

Build matrix is defined in **`build.yaml`** (Corne left/right + settings_reset for nice!nano).

---

## Flash firmware

1. Put the board in bootloader mode (double-tap reset).
2. Copy the `.uf2` file for each half to the **NICENANO** drive.

---

## Tools

- [ZMK](https://zmk.dev/) — firmware
- [Keymap editor](https://nickcoutsos.github.io/keymap-editor/) — visualize/edit keymaps
- [keymap-drawer](https://keymap-drawer.streamlit.app/) — draw keymap diagrams

---

## Adding more keyboards

Edit **`build.yaml`** and add entries under `include`. Example for Corne + Lily58:

```yaml
include:
  - board: nice_nano
    shield: corne_left
  - board: nice_nano
    shield: corne_right
  - board: nice_nano
    shield: lily58_left
  - board: nice_nano
    shield: lily58_right
```

Add the shield config and keymap files (e.g. `lily58.conf`, `lily58.keymap`) under **`config/`**. See [ZMK user setup](https://zmk.dev/docs/user-setup) and the comments in `build.yaml` for options like `artifact-name`, `snippet`, and `cmake-args`.

---

## Local setup (optional)

To build or develop locally with [ZMK tooling](https://zmk.dev/docs/user-setup):

```sh
# Install pipx and ZMK CLI
brew install pipx && pipx ensurepath
pipx install zmk

# Point ZMK at this repo and add keyboards
zmk config user.home "$(pwd)"
zmk keyboard add
```

Edit `config/*.conf` and `config/*.keymap`, then commit and push; CI will build, or download artifacts from [Actions](https://github.com/neversad-dev/zmk-config/actions).

---

## License

[MIT](LICENSE) — feel free to use and adapt this config.
