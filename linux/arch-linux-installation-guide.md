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
paru -S hyprland-git kitty zen-brownser-bin rofi nautilus waybar fastfetch stow less obsidian
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

## TO DO
- [ ] Updates the mirror list
- [ ] Dual boot FreeBSD
- [ ] hyprshot hyperlock hypridle
- [ ] Audio
