# Dual Boot
## 1  Dual boot FreeBSD - UEFI/GPT

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
$ sudo grub-mkconfig -o /boot/grub/grub.cfg
```
