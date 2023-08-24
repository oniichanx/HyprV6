# HyprV6 For TESTING Version 0.28.0
This is V6 of the Hyprland-git install script

It contains a collection of dot config files for hyprland with a simple install script.
IMPORTANT - This script is meant to run on a clean fresh Arch install on physical hardware

You can grab the config files and install packages by hand with the command listed below

Do this ONLY if you need Nvidia support (do this first)
```
yay -S linux-headers linux-zen linux-zen-headers nvidia-dkms qt5-wayland qt5ct libva libva-nvidia-driver-git

Add modules: nvidia nvidia_modeset nvidia_uvm nvidia_drm to /etc/mkinitcpio.conf

Generate new image: sudo mkinitcpio --config /etc/mkinitcpio.conf --generate /boot/initramfs-custom.img

Add/create the following: options nvidia-drm modeset=1 in /etc/modprobe.d/nvidia.conf

reboot!
```

Now install the below for Hyprland

```
yay -S hyprland kitty jq mako waybar-hyprland swww swaylock-effects \
wofi wlogout xdg-desktop-portal-hyprland swappy grim slurp thunar \
polkit-gnome python-requests pamixer pavucontrol brightnessctl bluez \
bluez-utils blueman network-manager-applet gvfs thunar-archive-plugin \
file-roller btop pacman-contrib starship ttf-jetbrains-mono-nerd \
noto-fonts-emoji lxappearance xfce4-settings sddm-git sddm-sugar-candy-git 
```

Or you can use the attached script | "set-hypr" | to install everything for you.
---
- #### | set-hypr | for hyprland aur version it slow for get new update but perfect to using daily
---

<details>
  <summary><strong> How to use attached script? </strong></summary>
  
- Step 1
```
  git clone https://github.com/oniichanx/hyprv5.git
```
- Step 2
```
  cd hyprv5
```
- Step 3
```
  chmod +x set-hypr
```
```
  chmod +x set-hypr-git
```
- Step 4 run which one you wanna use `hypr or hypr-git`
```
  ./set-hypr
```
```
  ./set-hypr-git
```
- DONE
---
</details>
</details>

<details>
  <summary><strong> After Done  Install optional packages? </strong></summary>

- #### Any Nerd Fonts installed and used by your terminal emulator to display icon (Highly Recommended: JetBrains Mono, since most of the config using this font)

- You can use lime-desu script to download any Nerd Fonts (requires [fzf](https://github.com/junegunn/fzf)&[wget](https://archlinux.org/packages/extra/x86_64/wget))
```
sudo pacman -S fzf wget
```
- run this next when fzf & wget install done
```
bash -c "$(curl -Ls https://raw.githubusercontent.com/lime-desu/bin/main/nf-dl)"
```
---
- #### install all font manual
```
pacman -S ttf-dejavu ttf-liberation ttf-droid ttf-ubuntu-font-family noto-fonts noto-fonts-cjk ttf-font-awesome

yay -S ttf-gelasio-ib ttf-caladea ttf-carlito ttf-liberation-sans-narrow ttf-ms-fonts ttf-tlwg
```
---
- #### install apple fonts manual
```
git clone https://aur.archlinux.org/apple-fonts.git
cd apple-fonts
makepkg -si
```
---
- #### install obs-studio & font-manager
```
pacman -S obs-studio
yay -S font-manager
```
---
- #### install webcord it just discord but can sharing srceen on wayland&hyprland
```
git clone https://aur.archlinux.org/webcord.git
cd webcord
makepkg -si
```
---
- #### install AppImageLauncher for just use appimage
```
yay -S AppImageLauncher
```
---
- #### install imagemagick for custom neofetch with image like .png|.jpg|.gif (requires [neofetch config](https://github.com/oniichanx/neofetch))
```
sudo pacman -S imagemagick
```
---
- #### set default-web-browser to librewolf
```
xdg-settings set default-web-browser librewolf.desktop
```
  </details>
</details>

<details>
  <summary><strong> How to dual boot windows with archlinux? </strong></summary>
  
---
- Step 1
```
sudo pacman -S os-prober
```
- Step 2
```
sudo mkinitcpio -P
```
- Step 3 remove # on GRUB_DISABLE_OS_PEROBER=false
```
sudo nano /etc/default/grub
```
- Step 4
```
sudo grub-install --target=x86_64-efi --efi-directory=/efi --boot-directory=/efi --bootloader-id=GRUB
```
- or
```
sudo grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB --boot-directory=/mnt/boot
```
- Step 5
```
sudo grub-mkconfig -o /efi/grub/grub.cfg
```
- Done

---
  </details>
</details>

<details>
  <summary><strong> How to make firefox glowie? </strong></summary>

(requires [hnhx config](https://github.com/hnhx/user.js) or [My config](https://github.com/oniichanx/neofetch/tree/main/firefox))

  </details>
</details>

<details>
  <summary><strong> How to make hyprland gaming? </strong></summary>
  
- #### Install steam
```
sudo pacman -S steam
```
---
- #### Install wine & lutris
```
sudo pacman -S --needed --noconfirm lutris wine-staging wine-mono
```
---
- #### Install lutris requires missed (NVIDIA)
```
sudo pacman -S --needed nvidia-dkms nvidia-utils lib32-nvidia-utils nvidia-settings vulkan-icd-loader lib32-vulkan-icd-loader
```
---
- #### if you want play minecraft
```
sudo pacman -S --needed --noconfirm cava vscodium-bin prismlauncher-qt5-bin
```
---
- #### if you want play game on windows (requires [StartWine](https://github.com/RusNor/StartWine-Launcher))
```
curl -sLo /dev/null -w '%{url_effective}' https://github.com/RusNor/StartWine-Launcher/releases/latest
copy output link
wget https://github.com/RusNor/StartWine-Launcher/releases/tag/StartWine_v***
chmod +x StartWine_v*
./StartWine_v37*
```
or Aur
```
yay -S --needed --noconfirm startwine
```
---
- #### if you want change wallpaper quick (requires [Waypaper](https://github.com/anufrievroman/waypaper))
```
sudo pacman -S --needed --noconfirm python-pip python-pipx swaybg
```
```
pip install waypaper
```
```
pipx install waypaper
```
Or use yay packages
```
yay -S waypaper-git
```
Add this line in your hyprland.conf
```
exec-once=waypaper --restore
```
Reboot
`waypaper` will run GUI application.

---

  </details>
</details>

<details>
  <summary><strong> You do wanna my wallpaper set? </strong></summary>
  
- ### ([Wallpaper Set](https://github.com/oniichanx/neofetch/tree/main/wallpaper))
</details>
</details>
