# Hyprland

## 1  Hyprland for Newbs

Tutorial series from [typecraft](https://www.youtube.com/@typecraft_dev)]

- [ ] You NEED to try Hyprland on Linux RIGHT NOW
- [ ] Don't use Hyprland without these AMAZING tools
- [ ] This might be my favorite Hyprland config ever!

## 2  Ricing Hyprland

Install Hyprland packages and [Useful Utilities](https://wiki.hypr.land/Useful-Utilities/)

```shell
$ yay -S \
	hyprland-git \
	kitty \
	brave-brownser \
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
	catppuccin-gtk-theme-mocha
	xdg-desktop-portal-hyprland-git \
	xdg-desktop-portal-gtk-git \
	qt5-wayland \
	qt6-wayland \
	wl-clipboard
```

Download and install fonts

```shell
$ sudo mkdir -p /usr/local/share/fonts/ttf

$ 7z x -oJetBrainsMono JetBrainsMono.zip
$ 7z x -oCascadiaCode CascadiaCode.zip

$ sudo mv JetBrainsMono /usr/local/share/fonts/ttf
$ sudo mv CascadiaCode /usr/local/share/fonts/ttf
```

Making Zsh your default shell

```shell
$ chsh -l
$ chsh -s /usr/bin/zsh
```

Clone dotfiles

```shell
$ mkdir developer
$ cd developer

$ git clone https://github.com/tachosx/dotfiles.git
$ git clone https://github.com/tachosx/vault.git
```

Manage dotfiles using GNU Stow

```shell
$ cd dotfiles

$ stow --target=$HOME hyprland
$ stow --target=$HOME kitty
$ stow --target=$HOME zsh
$ stow --target=$HOME bat
$ stow --target=$HOME cava
$ stow --target=$HOME nvim
$ stow --target=$HOME rofi
$ stow --target=$HOME starship
$ stow --target=$HOME wallpapers
$ stow --target=$HOME waybar
```

## 3  Catppuccin color scheme

- [ ] Rofi
- [ ] bat
- [ ] GRUB
- [ ] tty
- [ ] Brave Browser
- [ ] Obsidian
- [ ] GTK apps

## 4  Multimedia

- [ ] [Install PipeWire on Arch Linux](https://linuxgenie.net/install-pipewire-on-arch-linux/)