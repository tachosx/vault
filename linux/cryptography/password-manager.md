# Password manager

[The standard UNIX password manager](https://wiki.archlinux.org/title/Pass) is a simple password manager for the command line.
## 1  Basic usage

Generate a GnuPG key pair

```shell
$ gpg --full-gen-key
```

Initialize the password store

```shell
$ pass init gpg_key_id
```

Create a new password

```shell
$ pass insert github/access/token
```

Get a view of the password store

```shell
$ pass
```

Generate a new random password, where `n` is the desired password length.

```shell
$ pass generate github/access/token n
```

Retrieve a password

```shell
$ pass github/access/token
```

Retrieve the password directly onto the clipboard temporarily.

```shell
$ pass -c archlinux.org/wiki/username
```

## 2  Central Git server for pass in combination with GnuPG

You are able to setup a password management system by setting up a central Git server for pass. This allows you to synchronize your central password repository through multiple client environments.

This section assumes you have configured GnuPG and have a key pair to encrypt passwords. On your local client ensure you have a local password store on the client, then enable management of local changes through Git, add your remote Git repository, and push your local pass history.

Create a local password store

```shell
$ pass init gpg_key_id
```

Enable management of local changes through Git

```shell
$ pass git init
```

Add the remote git repository as 'origin'

```shell
$ pass git remote add origin https://github.com/username/.password-store.git
$ pass git branch -M main
```

Push your local pass history

```shell
$ pass git push -u --all
```

Now you can use the standard Git commands, prefixed by `pass`. For example: `pass git push`, or `pass git pull`. pass will automatically create commits when you use it to modify your password store.