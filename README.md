# 🌊 Kanagawa Hypr Dots 🌊
Collection of personal configs, desktop environment settings and editors preferences. Mostly based on [Simple Hyprland](https://github.com/gaurav23b/simple-hyprland/tree/879dba81c84134072826a21453c15e553d03da2d) and CachyOS defaults.

##### Key Changes
* [split monitor workspaces](https://github.com/Duckonaut/split-monitor-workspaces) plugin to assign distinct workspaces per monitor
* CONTROL as the mainMod key (it's less freaky than using SUPER and straining fingers all the time)
* Hardware cursor lag fix
* Color theme adjustments to match [Kanagawa Wave](https://github.com/rebelot/kanagawa.nvim) palette, rather than Catppuccin
* No Kvantum. QT and GTK applications styled by separate fine tuned themes via `ngw-look` and `qt6ct-kde`
* No includes, single `hypr.config` file
* No wlogout
* Minimal gaps between windows.
* Non-distracting, almost instant animations.

TODO: 
```
* Fix brightnessctl to control external monitor brightness levels.
* Kanagawa Wave GTK theme.
* Find a replacement for pavucontrol.
* LibreWolf theme.
* Waybar Weather / Now Playing Widget (?)
* Notifications daemon styling (perhaps use mako instead of dunst).
* Installation shell script.
```

<p align="center">
  <img src=".misc/.fetch.png" />
</p>


## Installation
These dots are not meant to be used by someone else, as they are highly customized to my personal preferences. However, if you are still willing to try, just clone the repo and replace the configs you are most interested in. Hopefully at some point there will be a shell installation script.

Additionally, check [Post Install Check List](https://github.com/shayaharuno/dotfiles/blob/master/CHECKLIST.md) for clean Arch + Hyprland installation

## Keybindings
* tofi - `ALT + SPACE`
* alacritty - `CTRL + BACKSLASH`
* kill active - `CTRL + Q`
* librewolf - `CTRL + B`
* obsidian - `CTRL + O`
* wlogout - `CTRL + ALT + DEL`
* keyboard layout switch - `SHIFT + ALT`
* disable all keybindings - `CTRL + HOME`
* select workspace - `CTRL + 1-5`
* switch workspace left / right - `CTRL + SHIFT + Arrow Left || Arrow Right`
* silently send to workspace - `CTRL + SHIFT + 1-5`
* logout - `CTRL + F12`
* kill waybar - `CTRL + SHIFT + F12`
* scratchpad - `SUPER + S`
* send to scratchpad - `SUPER + SHIFT + S`
* area screenshot - `SUPER + PGUP`
* fullscreen screenshot - `SUPER + PGDOWN`
* hyprpicker - `SUPER + P`
