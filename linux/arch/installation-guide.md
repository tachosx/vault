# Arch Installation Guide

## 1  Step by step guide

- [ ] [Arch Linux Installation Guide](https://github.com/radleylewis/arch_installation_guide)

MSI hot keys

```shell
To enter UEFI Firmware	DEL
To boot menu display	F11
```

Set the console keyboard layout and font

```shell
$ loadkeys la-latin1
$ setfont ter-120b
```

Set the timezone

```shell
$ timedatectl list-timezones | grep Mexico
$ timedatectl set-timezone America/Mexico_City
$ timedatectl set-ntp true
```

GPT disk partition layout

| Size             | Partition Type Code | Name                  |
| :--------------- | :-----------------: | :-------------------- |
| 1 GB             |        EF00         | EFI system partition  |
| 50 GB            |        A503         | FreeBSD UFS           |
| Rest of the disk |        8304         | Linux x86-64 root (/) |

Install essential packages

```shell
$ pacstrap -K \
	/mnt \
	base \
	linux \
	linux-firmware \
	linux-headers \
	neovim \
	sudo
```

Install main packages

```shell
$ pacman -S \
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

Make the console keyboard layout and font persistent. Add options to `/etc/vconsole.conf`.

```shell
KEYMAP=la-latin1
FONT=ter-120b
```

## 2  Set global environment variables

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

## 3  Updates the mirror list

- [ ] [Reflector](https://wiki.archlinux.org/title/Reflector)

## 4  Initialize zram devices

- [ ] [zram-generator](https://wiki.archlinux.org/title/Zram)

## 5  Security

- [ ] [Arch Linux Post Install Guide](https://www.youtube.com/watch?v=8Oz4CIB4YjU)

## 6  To Do

- [ ] Updates the mirror list
- [ ] Free up disk space
- [ ] SSH Hardening