# 🌊 Kanagawa Hypr Dots 🌊
Collection of personal configs, desktop environment settings and editors preferences. Mostly based on [Simple Hyprland](https://github.com/gaurav23b/simple-hyprland/tree/879dba81c84134072826a21453c15e553d03da2d).

##### Key Changes
* [split monitor workspaces](https://github.com/Duckonaut/split-monitor-workspaces) plugin to assign distinguish workspaces (four) per display
* F1-F4 to switch between workspaces
* CONTROL as mainMod key (it's less freaky than use SUPER and break fingers all the time)
* CONTROL + Digits || CONTROL + SHIFT + Arrows as an alternative method to switch between workspaces
* SUPER + S to use scratchpad
* Hardware cursor lag fix
* Color theme adjustments to match [Kanagawa Wave](https://github.com/rebelot/kanagawa.nvim) palette, rather than Catppuccin
* Kanagwa Wave theme for KDE applications (qt6ct-kde)
* Other minor fixes and tweaks

TODO: 
```
- Kanagawa Wave GTK theme
- Waybar Keyboard Layout Widget
- Waybar Power Button Widget
- Notifications daemon styling
```

<p align="center">
  <img src=".misc/.fetch.png" />
</p>


## Installation
1. Install [stow](https://github.com/aspiers/stow/) ```yay -S stow```

2. Clone repo and create symlinks
```sh
cd .dotfiles
stow .
```
In case of conflicts with already existing configs, use ```stow --adopt .```
