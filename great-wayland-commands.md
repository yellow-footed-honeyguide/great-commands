# 🪟 Wayland Utilities

| Utility | Description | Usage Example |
|---------|-------------|----------------|
| [wlr-randr](https://gitlab.freedesktop.org/emersion/wlr-randr) | Display configuration tool for wlroots-based compositors | `wlr-randr --output eDP-1 --mode 1920x1080` |
| [wl-clipboard](https://github.com/bugaevc/wl-clipboard) | Command-line copy/paste utilities for Wayland | `echo "Hello from Wayland" \| wl-copy`<br>`wl-paste` |
| [wayshot](https://github.com/waycrate/wayshot) | Screenshot tool for Wayland compositors | `wayshot -f screenshot.png` |
| [wev](https://git.sr.ht/~sircmpwn/wev) | Input event viewer for Wayland | `wev` |
| [wf-recorder](https://github.com/ammen99/wf-recorder) | Screen recording tool for Wayland compositors | `wf-recorder -f output.mp4` |
| [wtype](https://github.com/atx/wtype) | Xdotool-like tool for Wayland | `wtype "This is input text"` |
| [slurp](https://github.com/emersion/slurp) | Select a region in Wayland compositors | `slurp \| grim -g - screenshot.png` |
| [grim](https://github.com/emersion/grim) | Screenshot utility for Wayland | `grim screenshot.png` |
| [wob](https://github.com/francma/wob) | Lightweight overlay volume/backlight/progress bar for Wayland | `echo 50 > $SWAYSOCK.wob` |
| [wshowkeys](https://git.sr.ht/~sircmpwn/wshowkeys) | Displays pressed keys on screen | `wshowkeys` |
| [waypipe](https://gitlab.freedesktop.org/mstoeckl/waypipe) | Network transparency with Wayland | `waypipe ssh user@host application` |
