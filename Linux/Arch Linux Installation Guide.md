## Set global environment variables

Add below environment variables to `/etc/security/pam_env.conf` file

```
XDG_CONFIG_HOME DEFAULT=@{HOME}/.config
ZDOTDIR         DEFAULT=${XDG_CONFIG_HOME}/zsh
```

Add below environment variables to `/etc/environment` file

```
EDITOR=nvim
VISUAL=nvim
```

## Ricing Hyprland
## Tools and utilities
- [XDG user directories](https://wiki.archlinux.org/title/XDG_user_directories)
