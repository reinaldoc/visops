# visops
Visops: a wrapper to Mozilla SOPS like visudo.

## Requiments

- install SOPS: [https://github.com/mozilla/sops/releases](https://github.com/mozilla/sops/releases)
- generate or import GPG private key: gpg --import private.key
- export a existing public key fingerprint to re-encrypt file;
  - fingerprint must be listed on: gpg --list-keys

## Usage

```
  visops file.yml
```

## Errors

- Decrypt erros will be printed on console.
- Encrypt erros will be saved on $file.visops.tmp.error.
