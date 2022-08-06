# visops
Visops: a wrapper to Mozilla SOPS like visudo. SOPS is used to encrypt YAML
values.

Visops permit edit a encrypted file. Basicly we need decrypt file before
open text editor and encrypt after close text editor. A YAML file with
all values encrypted or those ones encrypted with **encrypted_regex** will
works, so detected regexp from existing file will br applied on encryption.

## Limitations

Visops use the first encrypted_regex that appear on YAML file to re-encrypt
the file. Then visops doesn't work with multi YAMLs on a single file that
use more then one regexp. Visops will alert you if that's the case.

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
