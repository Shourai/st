# st - simple terminal

st is a simple terminal emulator for X which sucks less.

## Notes about this fork

This is a fork of st, the original repo can be found here: [https://git.suckless.org/st/](https://git.suckless.org/st/)

The original st webpage is here: [https://st.suckless.org/](https://st.suckless.org/)

### Available patches

* [Alpha](https://st.suckless.org/patches/alpha/) : This patch allows users to change the opacity of the background. Note that you need an X composite manager (e.g. compton, xcompmgr) to make this patch effective.
* [Clipboard](https://st.suckless.org/patches/clipboard/) : This trivial patch sets CLIPBOARD on selection.
* [font2](https://st.suckless.org/patches/font2/) : This patch allows to add spare font besides default.
* [Wide glyph](https://st.suckless.org/patches/glyph_wide_support/) : This patch allows to display the full glyph instead of it being cut off. See also [here](https://github.com/LukeSmithxyz/st/pull/349)

#### Colorscheme patch
The colorscheme patch is a custom patch, it is not the ones from [colorscheme](https://st.suckless.org/patches/colorschemes/)
It is `solarized.dark` exported from https://terminal.sexy with a different bg and fg color.
Also the `defaultfg`, `defaultbg` and `defaultcs` are not `static`s, otherwise it won't compile.

### Previous available patches

* [Fix Keyboard Input](https://st.suckless.org/patches/fix_keyboard_input/) : Add a few previously undefined keys.
Removed as this was used for additional keys for zooming.

### Applying/Removing Patches
Applying patches from this repository use:

- applied all at once without committing:
```
git apply patches/*
```

- applied as individual commits
```
git am patches/*
```

Applying patches from https://st.suckless.org/patches/ use:
```
# Add custom patch
patch -Np1 -i patches/custom.diff
or
patch < patch.diff

# Remove st-alpha-201806-16-0.81 patch
patch -R patches/st-alpha-20180616-0.8.1.diff
```

## Requirements

In order to build st you need the Xlib header files.

## Installation

Edit config.mk to match your local setup (st is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install st (if
necessary as root):

```bash
make clean install
```

## Running st

Start `st` from a launcher like dmenu or rofi.

If you did not install st with make clean install, you must compile
the st terminfo entry with the following command:

```bash
tic -sx st.info
```

See the man page for additional details.

### Keyboard Shortcuts
Action      | Key Combination
---         | ---
Copy        | `ctrl` + `shift` + `c`
Paste       | `ctrl` + `shift` + `v`
Zoom In     | `ctrl` + `shift` + `PageUp`
Zoom Out    | `ctrl` + `shift` + `PageDown`
Reset Zoom  | `ctrl` + `shift` + `Home`

## Credits

* Forked from [https://st.suckless.org/](https://st.suckless.org/)
* Based on Aurélien APTEL aurelien.aptel@gmail.com bt source code.
