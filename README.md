# Corne ZMK config

Corne LP is a low profile split 40% keyboard

## My Corne Cherry v3 setup

- ✅	[Corne LP V3 PCB Black](https://www.boardsource.xyz/products/Corne_LP)
- ✅	[nice!nano v2.0](https://nicekeyboards.com/docs/nice-nano/)
- ✅	[Choc Hot Swap Sockets](https://www.boardsource.xyz/products/Choc_Hot_Swap_Sockets)
- ✅	[Choc Purpz switches](https://www.boardsource.xyz/store/5ef6f7376786dc1e65a80744)
- ✅	[Choc Robin switches](https://www.amazon.com/Profile-Mechanical-Switch-Keyboard-Switches/dp/B0CKGLZ3BW)
- ✅	[MBK blanks keycaps](https://www.boardsource.xyz/products/MBK_blanks)
- ✅	Space Grey Aluminum Corne LP Case


## Tool

- [ZMK](https://zmk.dev/)
- [Keymap editor web](https://nickcoutsos.github.io/keymap-editor/)
- [keymap-drawer web](https://keymap-drawer.streamlit.app/)

## Build firmware

GitHub Actions is used to automatically build the user's configured firmware for them.

1. Push the changes to repository
2. Go to [Actions](https://github.com/GiveNoCode/zmk-config/actions) 
3. Wait for build completion
4. Download artifacts -> firmware.zip


## Flash firmware

1. Enter bootloader (double tap reset)
2. Copy .uf2 firmware (for each half) file to "NICENANO" root folder

## Building Additional Keyboards

You can build additional keyboards with GitHub actions by appending them to `build.yml` in your `zmk-config` folder. For instance assume that we have set up a Corne shield with nice!nano during [initial setup](https://zmk.dev/docs/user-setup) and we want to add a Lily58 shield with nice!nano v2. The following is an example `build.yaml` file that would accomplish that:

```
include:  
	- board: nice_nano    
	  shield: corne_left  
	- board: nice_nano    
	  shield: corne_right  
	- board: nice_nano_v2   
	  shield: lily58_left  
	- board: nice_nano_v2    
	  shield: lily58_right
```

In addition to updating `build.yaml`, Lily58's shield files should also be added into the `config` sub-folder inside `zmk-config` together with your Corne files, e.g.:

```
corne.conf
corne.keyma
plily58.conf
lily58.keymap
```

## Initial setup

source: [initial setup](https://zmk.dev/docs/user-setup)

1. Install pipx - python package manager

```sh
brew install pipx
pipx ensurepath
```

2. Install zmk - tool for creating keyboards

```sh
pipx install zmk
```

3. Init repository

```sh
zmk init
```

4. or setup with existing repo

```sh
zmk config user.home "/path/to/zmk-config"
```

5. Add a keyboard

```sh
zmk keyboard add
```

6. Adjust a .conf nd .keymap file

7. commit and push changes

8. Download github actions artifact and flash
