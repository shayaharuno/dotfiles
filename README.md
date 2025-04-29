# 🌊 Kanagawa Hypr Dots 🌊
Collection of personal configs, desktop environment settings and editors preferences. Mostly based on [Simple Hyprland](https://github.com/gaurav23b/simple-hyprland/tree/879dba81c84134072826a21453c15e553d03da2d).

##### Key Changes
* [split monitor workspaces](https://github.com/Duckonaut/split-monitor-workspaces) plugin to assign distinguish workspaces (four) per display
* F1-F4 to switch between workspaces
* CONTROL as mainMod key (it's less freaky than use SUPER and break fingers all the time)
* Hardware cursor lag fix
* Color theme adjustments to match [Kanagawa Wave](https://github.com/rebelot/kanagawa.nvim) palette, rather than Catppuccin
* No Kvantum. QT and GTK applications styled by separate fine tuned themes via ngw-look and qt6ct-kde
* Single hypr.config file, includes are for sickfucks

TODO: 
```
- Kanagawa Wave GTK theme
- Find replacement for pavucontrol
- LibreWolf theme
- Waybar Power Button Widget (?)
- Waybar Weather / Now Playing Widget (?)
- Notifications daemon styling
- Installation shell script
```

<p align="center">
  <img src=".misc/.fetch.png" />
</p>


## Installation
These dots are not meant to be used by someone else, as they are highly customized to my personal preferences. However, if you are still willing to try, just clone the repo and replace the configs you are most interested in.

## Keybindings
* `ALT + SPACE` - tofi
* `CTRL + BACKSLASH` - terminal
* `CTRL + Q` - kill active
* `CTRL + B` - browser
* `CTRL + O` - obsidian
* `CTRL + ALT + DEL` - wlogout menu
* `SHIFT + ALT` - switch keyboard layout
* `CTRL + HOME` - turn on/off all keybindings
* `F(1-4)` or `CTRL + 1-4` - select workspace 1-4
* `CTRL + SHIFT + Arrow Left || Arrow Right` - switch workspace left / right
* `CTRL + SHIFT + 1-4` - silently send to workspace 1-4
* `CTRL + F12` - logout
* `CTRL + SHIFT + F12` - kill waybar
* `SUPER + S` - scratchpad
* `SUPDER + SHIFT + S` - send to scratchpad
