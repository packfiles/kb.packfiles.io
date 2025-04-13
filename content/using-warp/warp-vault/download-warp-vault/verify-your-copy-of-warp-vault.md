---
icon: signature-lock
---

# Verify Your Copy of Warp Vault

Packfiles takes the security of our products and protection of our customers extremely seriously.

To prevent tampering, all Warp Vault releases are cryptographically signed using industry-standard techniques. To verify the authenticity and integrity of your Warp Vault download, we recommend following the steps below for your host operating system.

{% hint style="danger" %}
If you experience a verification failure for a Warp Vault release and suspect tampering, please notify the Packfiles Security Team immediately at [security@packfiles.io](mailto:security@packfiles.io).
{% endhint %}

Jump to instructions for:

* [macOS](verify-your-copy-of-warp-vault.md#macos)
* [Windows](verify-your-copy-of-warp-vault.md#windows)
* [Linux](verify-your-copy-of-warp-vault.md#linux)

### macOS

On macOS systems, the code signature of Warp Vault can be inspected with the following command:

```
codesign -dv --verbose=4 /Path/To/Your/Copy/Of/Warp\ Vault.app
```

This will produce output similar to the below. Verify that the `Authority` field matches `Developer ID Application: Packfiles Inc (LQ28J3F3JH)`, and that the `TeamIdentifier` field matches `LQ28J3F3JH`.

```
Executable=/Applications/Warp Vault.app/Contents/MacOS/Warp Vault
Identifier=io.packfiles.vault
Format=app bundle with Mach-O universal (x86_64 arm64)
CodeDirectory v=20500 size=99230 flags=0x10000(runtime) hashes=3090+7 location=embedded
VersionPlatform=1
VersionMin=720896
VersionSDK=918784
Hash type=sha256 size=32
CandidateCDHash sha256=ba7c6219f8c7eb29db4f6e80d00364acaff85b1a
CandidateCDHashFull sha256=ba7c6219f8c7eb29db4f6e80d00364acaff85b1a0b832b6fd54663aeda53e0c8
Hash choices=sha256
CMSDigest=ba7c6219f8c7eb29db4f6e80d00364acaff85b1a0b832b6fd54663aeda53e0c8
CMSDigestType=2
Executable Segment base=0
Executable Segment limit=7553024
Executable Segment flags=0x1
Page size=4096
CDHash=ba7c6219f8c7eb29db4f6e80d00364acaff85b1a
Signature size=9046
Authority=Developer ID Application: Packfiles Inc (LQ28J3F3JH)
Authority=Developer ID Certification Authority
Authority=Apple Root CA
Timestamp=Apr 9, 2025 at 18:47:11
Info.plist entries=14
TeamIdentifier=LQ28J3F3JH
Runtime Version=14.5.0
Sealed Resources version=2 rules=13 files=3
Internal requirements count=1 size=180
```

### Windows

On Windows, you can inspect the certificate chain of Warp Vault's MSIX installer or .exe file to verify its authenticity.

Right click on your downloaded copy of the Warp Vault installer and select **Properties**.

<figure><img src="../../../.gitbook/assets/image (117).png" alt="" width="375"><figcaption></figcaption></figure>

In the Properties view, select **Digital Signatures**, then click on **Details**.

<figure><img src="../../../.gitbook/assets/image (119).png" alt="" width="375"><figcaption></figcaption></figure>

In the Details view, select **Advanced**. Verify that the **Serial number** field of the signature has a value of `67d7636c9135682d620110e6`.

<figure><img src="../../../.gitbook/assets/image (120).png" alt="" width="375"><figcaption></figcaption></figure>

### Linux

Linux builds of Warp Vault are signed with the _Packfiles' Vault Linux Releases (A)_ PGP key. This key's fingerprint is:

```yaml
ED67E8E35FB2EB52F6C81937BD4C2E3452360800
```

The public key is:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----

mDMEZ+GTMBYJKwYBBAHaRw8BAQdA/21kfksEyK2OvVPEJ7uUX31gluDDw9P/3WjX
lQ+8pkq0S1BhY2tmaWxlcyBJbmMgQ29kZSBTaWduaW5nIDxzZWN1cml0eUBwYWNr
ZmlsZXMuaW8+IChWYXVsdCBMaW51eCBSZWxlYXNlcyBBKYiTBBMWCgA7FiEE7Wfo
41+y61L2yBk3vUwuNFI2CAAFAmfhkzACGwEFCwkIBwICIgIGFQoJCAsCBBYCAwEC
HgcCF4AACgkQvUwuNFI2CAB2oAEA4n+dkaQtfL1U3tuEiP+xpv92OACuAXaLSo2H
uYUFWIMBAJIlXlE53fZWq5C6Goiy/STYxQ5jmeelLWrNx76DX3sBuDMEZ+GTbxYJ
KwYBBAHaRw8BAQdAmiYHAlbiHQ6A93nMua18iKzXYGy6YRVEhlxB58o+A3OI7wQY
FgoAIBYhBO1n6ONfsutS9sgZN71MLjRSNggABQJn4ZNvAhsCAIEJEL1MLjRSNggA
diAEGRYKAB0WIQRJXfnXxwZbp3cfDD0iGqVnQtjAAwUCZ+GTbwAKCRAiGqVnQtjA
A2kxAQDuB95zcjk7qbmb3+MIvrs3G/3DWgjeLGyGur8zgqFzXwEAi9LX4o1mGFmq
TtkYxE+f2+RA10VlTp5CMXlUe5dr2A0cDQEAlhwlw6aQr0ljMGWyanLJSh0les90
3uleRsO29jMweCYA/3ycEqwlneaKtlLSDZgi2C03dGuK2n3aRVX+woHn5KQE
=Hc3u
-----END PGP PUBLIC KEY BLOCK-----
```

You can check the signature of a given Warp Vault release with the following process.

#### 1. Import the Key

Save the PGP public key block above to a file on disk. Then run:

```
gpg --import /path/to/the/public_key.pub
```

#### 2. Verify the Signature

After downloading a Linux release of Warp Vault, extract the contents of the archive and run the following command to verify the signature.

```
gpg --verify '/path/to/your/Warp Vault.sig' '/path/to/your/Warp Vault'
```

You should see output like the following:

```
gpg: Signature made Mon Mar 24 14:38:25 2025 EDT
gpg:                using EDDSA key 495DF9D7C7065BA7771F0C3D221AA56742D8C003
gpg: Good signature from "Packfiles Inc Code Signing <security@packfiles.io> (Vault Linux Releases A)" [unknown]
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: ED67 E8E3 5FB2 EB52 F6C8  1937 BD4C 2E34 5236 0800
     Subkey fingerprint: 495D F9D7 C706 5BA7 771F  0C3D 221A A567 42D8 C003
```

In the output from the verification command, ensure that the **Primary key fingerprint** field matches the _Packfiles' Vault Linux Releases (A)_ PGP key fingerprint of `ED67E8E35FB2EB52F6C81937BD4C2E3452360800`.

{% hint style="success" %}
You can safely ignore the `This key is not certified with a trusted signature!`message in the verification output. This message is related to whether the Packfiles PGP key is marked as trusted in your local GPG trust store, and has no bearing on the validity of the PGP signature for the Warp Vault executable.
{% endhint %}
