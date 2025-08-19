# GnuPG

[GnuPG](https://wiki.archlinux.org/title/GnuPG) allows you to encrypt and sign your data and communications.
## 1  Basic usage

Generate a key pair

```shell
$ gpg --full-gen-key
```

List keys in your public key ring

```shell
$ gpg --list-keys
```

List keys in your secret key ring

```shell
$ gpg --list-secret-keys
```

## 2  Export your public key

In order for others to send encrypted messages to you, they need your public key. To generate an ASCII version of a user's public key to file `public-key.asc` .

```shell
$ gpg --export --armor --output public-key.asc user-id
```

## 3  Import a public key

In order to encrypt messages to others, as well as verify their signatures, you need their public key. Import a public key with file name `public-key.asc` to your public key ring.

```shell
$ gpg --import public-key.asc
```

## 4 Encrypt and decrypt

You need to import a public key of a user before encrypting (option `-e`/`--encrypt`) a file or message to that recipient (option `-r`/`--recipient`).

Encrypt a file with the name doc

```shell
$ gpg --recipient user-id --encrypt doc
```

Decrypt (option `-d`/`--decrypt`) a file with the name doc.gpg encrypted with your public key.

```shell
$ gpg --output doc --decrypt doc.gpg
```

## 5  Backup your private key

Backup your private key

```shell
$ gpg --export-secret-keys --armor --output private-key.asc user-id
```

 Import the backup of your private key

```shell
$ gpg --import private-key.asc
```

## 6  Edit your key

Running the `gpg --edit-key user-id` command will present a menu which enables you to do most of your key management related tasks.

Type `help` in the edit key sub menu to show the complete list of commands.