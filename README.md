# visops
Visops: a wrapper to Mozilla SOPS like visudo.

Visops permit edit a encrypted file, just decrypt before open text editor,
and encrypt after close text editor.

## Requiments

- install SOPS
  - [https://github.com/mozilla/sops/releases](https://github.com/mozilla/sops/releases)

- generate or import GPG private key
  - gpg --import private.key

- export a existing public key fingerprint to re-encrypt file
  - fingerprint must be listed on: gpg --list-keys
  - export VISOPS_FINGERPRINT=40CHARSSTRING

- choose you text editor
  - export EDITOR=joe

## Usage

```
  visops file.yml
```

## Errors

- Decrypt erros will be printed on console.
- Encrypt erros will be saved on $file.visops.tmp.error.
