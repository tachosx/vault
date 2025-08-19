# Arch Linux Installation Guide

## MSI hot keys

```shell
To enter UEFI Firmware	DEL
To boot menu display	F11
```

## Step-by-step guide

[Arch Linux Installation Guide](https://github.com/radleylewis/arch_installation_guide)
[Arch Linux Post Install Guide | Linux Security](https://www.youtube.com/watch?v=8Oz4CIB4YjU)

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
| 50 GB            |        A503         | FreeBSD UFS           |
| Rest of the disk |        8304         | Linux x86-64 root (/) |

## Install essential packages

```shell
pacstrap -K /mnt base linux linux-firmware linux-headers neovim sudo
```

## Install main packages

```shell
pacman -S \
	btrfs-progs \
	grub \
	grub-btrfs \
	efibootmgr \
	networkmanager \
	git \
	reflector \
	amd-ucode \
	terminus-font \
	firewalld
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
[Reflector](https://wiki.archlinux.org/title/Reflector)

## Initialize zram devices
[zram-generator](https://wiki.archlinux.org/title/Zram)

## Ricing Hyprland

Install Hyprland packages

```shell
yay -S \
	hyprland-git \
	kitty \
	zen-brownser-bin \
	rofi-wayland \
	nautilus \
	waybar \
	fastfetch \
	stow \
	less \
	obsidian \
	7zip \
	zsh \
	zsh-syntax-highlighting \
	zsh-autosuggestions \
	zsh-history-substring-search \
	zsh-vi-mode \
	starship \
	lsd \
	bat \
	cava \
	unimatrix \
	yazi \
	ttf-font-awesome \
	hyprshot \
	hyperlock-git \
	hypridle \
	hyprpaper-git \
	htop \
	swaync \
	brightnessctl \
	nwg-look \
	xdg-desktop-portal-hyprland-git \
	xdg-desktop-portal-gtk-git \
	qt5-wayland qt6-wayland \
	wl-clipboard
```

Download and install fonts

```shell
sudo mkdir -p /usr/local/share/fonts/ttf
7z x -oJetBrainsMono JetBrainsMono.zip
7z x -oCascadiaCode CascadiaCode.zip
sudo mv JetBrainsMono /usr/local/share/fonts/ttf
sudo mv CascadiaCode /usr/local/share/fonts/ttf
```

Making Zsh your default shell

```shell
chsh -l
chsh -s /usr/bin/zsh
```

Clone dotfiles

```shell
mkdir developer
cd developer
git clone https://github.com/tachosx/dotfiles.git
git clone https://github.com/tachosx/vault.git
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

[Must have](https://wiki.hyprland.org/Useful-Utilities/Must-have/)

## Catppuccin color scheme

- Rofi
- bat
- GRUB
- tty
- Brave Browser
- Zen Browser
- Obsidian

## Multimedia

[Install PipeWire on Arch Linux](https://linuxgenie.net/install-pipewire-on-arch-linux/)

## Dual boot FreeBSD - UEFI/GPT

Add menuentry to  `/etc/grub.d/40_custom`

```shell
menuentry "FreeBSD" {
	insmod ufs2
	set root='(hd0,gpt2)'
	chainloader /boot/loader.efi
}
```

Generate GRUB configuration file

```shell
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

## To Do
- [ ] [[#Updates the mirror list]]
- [ ] Free up disk space
- [ ] SSH Hardening