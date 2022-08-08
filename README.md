# visops
Visops is a wrapper to Mozilla SOPS like visudo is for sudoers. SOPS is used
to encrypt YAML values.

Visops permits a user to edit an encrypted file. Basically we need to
decrypt the file before opening the text editor and encrypt the file after
closing the text editor.

A YAML file with all values encrypted or those ones encrypted with
**encrypted_regex** will work, so detected regexp from the existing file
will be applied on encryption.

## Requiments

- Install SOPS
  - [https://github.com/mozilla/sops/releases](https://github.com/mozilla/sops/releases)

- Generate or import GPG private key
  - gpg --import private.key

## Optional environment variables

Visops uses same fingerprint available on sops signature to identify public
key to encrypt the file. If you want encrypt the file with a new public key,
you must set **$VISOPS_FINGERPRINT**.

The fingerprint must be listed on: **gpg --list-keys**.

- Use other fingerprint
  - export VISOPS_FINGERPRINT=40CHARSSTRING

- Choose you text editor
  - export EDITOR=joe

## Usage

```
  visops file.yml
```

## Errors

- Decrypt errors will be printed on console.
- Encrypt errors will be saved on $file.visops.tmp.error.

## Limitations

Visops uses the first encrypted_regex that appears on YAML file to
re-encrypt the file. Then visops doesn't work with multi YAMLs on a single
file that uses more than one regexp. Visops will alert you if that's the
case.

