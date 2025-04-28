##### General
* BTRFS*: `@.snapshots` subvolume is not needed for Timeshift snapshots
* Enable periodic TRIM 
```sh 
 sudo systemctl enable fstrim.timer
 ```
 
* Edit `/etc/makepkg.conf` to disable debug packages
* Edit `/etc/pacman.conf` to enable colors, parallel downloads and `multilib` repo
* Edit `~/.config/hypr/hyprland.conf` to setup dual-monitor environment: [Wiki Page](https://wiki.hyprland.org/Configuring/Monitors/) (could be skipped if using dotfiles)
* Consider lowering `TimeouStopSec` in `/usr/lib/systemd/system/user@.service` to prevent slow shutdowns

* Install reflector and update mirror list
```sh
sudo pacman -S reflector
reflector --latest 5 --sort rate --save /etc/pacman.d/mirrorlist
```

* Enable Bluetooth service
```sh
sudo systemctl enable --now bluetooth.service
```

* Install [yay](https://github.com/Jguer/yay)
```sh
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

* Generate AUR db and make system upgrade
```sh 
yay -Y --gendb && yay
```

* Install required and essential packages
```sh
yay -S --needed kitty fish librewolf-bin stow git-credential-manager nvidia-open-dkms nvidia-utils egl-wayland pipewire wireplumber sddm wl-clipboard tar kate dolphin
```

* Install fonts
```sh
yay -S ttf-jetbrains-mono-nerd ttf-mplus-nerd font-inter
```

* Set fish as default shell (reboot required)
```sh
chsh -s /usr/bin/fish
```

* Consider removing Dolphin in favor of ranger
```sh
yay -R dolphin && yay -S ranger
yay -Ycc
```

* Configure [git-credential-manager](https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/install.md) (install pass and create passkey if needed)
```sh
git-credential-manager configure
git-credential-manager github login
```

* Clone dotfiles and make symlinks (use `stow --adopt .` in case of conflicting configs)
```sh 
git clone https://github.com/shayaharuno/dotfiles.git && cd dotfiles && stow .
```

* Install additional packages 
```sh
yay -S --needed aseprite-bin blender krita godot blender visual-studio-code-bin ncspot steam keepassxc telegram-desktop qbittorrent obs-studio discord neovim ark rnote vlc kcalc
```

##### Hyprland
* Install essential packages
```sh
yay -S --needed hyprland xdg-desktop-portal-hyprland polkit-kde-agent qt5-wayland qt6-wayland dunst qt5ct-kde qt6ct-kde nwg-look grimblast-git
```

* Add autostart parameters to `~/.config/hypr/hyprland.conf` (skip if using dotfiles)
```
exec-once=/usr/lib/polkit-kde-authentication-agent-1
exec-once=/usr/bin/dunst
exec-once=hyprpm reload -n
```

* Add hyprland specific environment variables to `~/.config/hypr/hyprland.conf`  (skip if using dotfiles)
```
env = LIBVA_DRIVER_NAME,nvidia
env = __GLX_VENDOR_LIBRARY_NAME,nvidia

# QT
env = QT_QPA_PLATFORM,wayland;xcb
env = QT_QPA_PLATFORMTHEME,breeze
env = QT_WAYLAND_DISABLE_WINDOWDECORATION,1
env = QT_AUTO_SCREEN_SCALE_FACTOR,1

# Toolkit Backend Variables
env = GDK_BACKEND,wayland,x11,*
env = SDL_VIDEODRIVER,wayland
env = CLUTTER_BACKEND,wayland

# XDG Specifications
env = XDG_CURRENT_DESKTOP,Hyprland
env = XDG_SESSION_TYPE,wayland
env = XDG_SESSION_DESKTOP,Hyprland
```

* Disable hardware cursors (IMPORTANT!) to prevent huge lags on external monitors `~/.config/hypr/hyprland.conf`  
```
cursor {
    no_hardware_cursors = true
}

```

* Update hyprpm and install [split-monitor-workspaces](https://github.com/Duckonaut/split-monitor-workspaces) plugin
```sh
hyprpm update
hyprpm add https://github.com/Duckonaut/split-monitor-workspaces
hyprpm enable split-monitor-workspacesplugin
hyprpm reload
```

* To configure QT apps appearance use `qt6ct-kde` and `qt5ct-kde` instead of ~~qt6ct~~ and ~~qt5ct~~ since those packages aren't patched to work properly with Dolphin and the rest of KDE apps

* Use `nwg-look` to configure appearance of GTK apps

##### GRUB
 * Uncommenting `GRUB_TERMINAL_OUTPUT=console` in `/etc/default/grub` fixes slow GRUB
 * `GRUB_GFXMODE=1440x900x32,1280x1024x32,auto` makes text larger and fixes slowdowns
 * Boot flags: `quiet splash loglevel=3 systemd.show_status=auto rd.udev.log_level=3 mitigations=off nowatchdog`
 * Apply changes: `grub-mkconfig -o /boot/grub/grub.cfg`

##### Environment Variables
 * Put user-specific enironment variables to `~/.bash_profile`
 * Fix fractional scaling:
   ```
   export QT_SCALE_FACTOR_ROUNDING_POLICY=RoundPreferFloor
   export STEAM_FORCE_DESKTOPUI_SCALING=1.5
   ```

##### Intel Graphics
 * Vulkan driver: `yay -S vulkan-intel lib32-vulkan-intel`
 * Video acceleration: `yay -S intel-media-driver onevpl-intel-gpu libva-utils`

##### NVIDIA Graphics
 * For 2000+ series cards install `nvidia-open-dkms`, otherwise use `nvidia-dkms`
 * In case of poor performance add `nvidia-boost.service` to `/etc/systemd/system` and enable it `sudo systemctl enable --now nvidia-boost`. Adjust clocks in `nvidia-boost.service` based on output of `nvidia-smi -q -d SUPPORTED_CLOCKS` if needed.
 * Enable HDR: `export KWIN_DRM_ALLOW_NVIDIA_COLORSPACE=1` in `/etc/environment/`
 * Video acceleration: `yay -S libvdpau libva-nvidia-driver`
* Some kernel flags that might be useful (Add these to `/etc/modprobe.d/nvidia.conf`)
```
# Suspend fix
options nvidia NVreg_PreserveVideoMemoryAllocations=1
options nvidia NVreg_TemporaryFilePath=/var/tmp
# Setting it to 0 might help with slowdowns, setting it to 1 only works for 2000+ cards
options nvidia NVreg_EnableGpuFirmware=1
# Wayland fix
options nvidia_drm modeset=1
options nvidia_drm fbdev=1
```

##### Wine
 * Install: `yay -S wine wine-mono winetricks`
 * Install fonts: `winetricks allfonts`
 * Shutdown hang workaround: run `winecfg` and add `winedevice.exe` library then disable it

##### Steam
 * It's possible to use NTFS partition for game library
 * In that case move `compatdata` to Linux fs and symlink it with NTFS library

##### Censorship
 * Spoofdpi: `yay -S spoofdpi-bin` then enable with `sudo systemctl enable --now spoofdpi.service` and add `--proxy-server=http://127.0.0.1:8080` to Chromium-based browsers
 * Mullvad: `yay -S mullvad-vpn-bin shadowsocks-rust shadowsocks-v2ray-plugin v2ray`
 * To circumvent API access issues run `mullvad-exclude sslocal -s 193.138.7.132:1300 -k mullvad -m chacha20-ietf-poly1305 -b 127.0.0.1:1080 --tcp-fast-open --tcp-no-delay --plugin v2ray-plugin --plugin-opts 'mode=quic;host=fi-hel-br-101.relays.mullvad.net'` and add `SOCKS5 remote` method at `127.0.0.1:1080`
 * After signing in set tunnel protocol to WireGuard and obfuscation to Shadowsocks
 * Create `/etc/sysctl.d/network.conf`:
```
net.core.rmem_max = 7500000
net.core.wmem_max = 7500000
```