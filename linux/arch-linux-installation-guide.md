# Arch Linux Installation Guide
## Dual boot FreeBSD - UEFI/GPT

Add below menuentry to  `/etc/grub.d/40_custom`

```shell
menuentry "FreeBSD" {
	insmod ufs2
	set root='(hd0,gpt2)'
	chainloader /boot/loader.efi
}
```

## Set global environment variables

Add below environment variables to `/etc/security/pam_env.conf` file

```shell
XDG_CONFIG_HOME DEFAULT=@{HOME}/.config
ZDOTDIR         DEFAULT=${XDG_CONFIG_HOME}/zsh
```

Add below environment variables to `/etc/environment` file

```shell
EDITOR=nvim
VISUAL=nvim
```

## Ricing Hyprland
## Tools and utilities
- [XDG user directories](https://wiki.archlinux.org/title/XDG_user_directories)
