# Arch Linux Installation Guide

## MSI hot keys
```shell
To enter UEFI Firmware	DEL
To boot menu display	F11
```

## Step-by-step guide on manually
[Arch Install](https://github.com/radleylewis/arch_installation_guide)

## Set the console keyboard layout and font
```shell
loadkeys la-latin1
setfont ter-120b
```

## Set the timezone
```shell
timedatectl list-timezones | grep Mexico
timedatectl set-timezone America/Mexico_City
timedatectl set-ntp true
```

## GPT disk partition layout

| Size             | Partition Type Code | Name                  |
| :--------------- | :-----------------: | :-------------------- |
| 1 GB             |        EF00         | EFI system partition  |
| 400 GB           |        8304         | Linux x86-64 root (/) |
| Rest of the disk |        A503         | FreeBSD UFS           |

## Install essential packages
```shell
pacstrap -K /mnt base linux linux-firmware linux-headers neovim sudo
```

## Install main packages
```shell
pacman -S btrfs-progs grub grub-btrfs efibootmgr networkmanager git reflector amd-ucode terminus-font firewalld
```

## Make the console keyboard layout and font persistent

Add options to `/etc/vconsole.conf`

```shell
KEYMAP=la-latin1
FONT=ter-120b
```

## Set global environment variables

Add environment variables to `/etc/environment` file

```shell
EDITOR=nvim
VISUAL=nvim
```

Add environment variables to `/etc/security/pam_env.conf` file

```shell
XDG_CONFIG_HOME DEFAULT=@{HOME}/.config
ZDOTDIR         DEFAULT=${XDG_CONFIG_HOME}/zsh
```

## Updates the mirror list
```shell
To Do
```

## Initialize zram devices
[zram-generator](https://wiki.archlinux.org/title/Zram)

## Ricing Hyprland

Install Hyprland packages

```shell
paru -S hyprland-git kitty zen-brownser-bin rofi-wayland nautilus waybar fastfetch stow less obsidian 7zip zsh zsh-syntax-highlighting zsh-autosuggestions zsh-history-substring-search zsh-vi-mode starship lsd bat cava unimatrix yazi ttf-font-awesome
```

Download and install fonts

```
sudo mkdir -p /usr/local/share/fonts/ttf
7z x -oJetBrainsMono JetBrainsMono.zip
sudo mv JetBrainsMono /usr/local/share/fonts/ttf

```

Making Zsh your default shell

```
chsh -l
chsh -s /usr/bin/zsh
```

Clone dotfiles

```shell
mkdir developer
cd developer
git clone https://github.com/tachosx/dotfiles.git
```

Manage dotfiles using GNU Stow

```shell
cd dotfiles
stow --target=$HOME hyprland
stow --target=$HOME kitty
stow --target=$HOME zsh
stow --target=$HOME bat
stow --target=$HOME cava
stow --target=$HOME nvim
stow --target=$HOME rofi
stow --target=$HOME starship
stow --target=$HOME wallpapers
stow --target=$HOME waybar
```

## Themes

```
git clone https://github.com/catppuccin/rofi.git
cd rofi/basic
sh install.sh
```

## Tools and utilities
- [XDG user directories](https://wiki.archlinux.org/title/XDG_user_directories)

## Dual boot FreeBSD - UEFI/GPT

Add menuentry to  `/etc/grub.d/40_custom`

```shell
menuentry "FreeBSD" {
	insmod ufs2
	set root='(hd0,gpt3)'
	chainloader /boot/loader.efi
}
```

Generate GRUB configuration file

```shell
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

## To Do
- [ ] Updates the mirror list
- [ ] hyprshot hyperlock hypridle
- [ ] Audio
- [ ] Free up disk space