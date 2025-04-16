---
icon: bitbucket
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Bitbucket Server

The Bitbucket Server credential type stores the credentials and configuration associated with the Bitbucket Server instance from which you're migrating data with Warp.

To configure a Bitbucket Server credential, you'll need:

* A Username and Password for a Bitbucket Server account with Admin or Super Admin permissions,
* At least one storage bucket, and
* SFTP or SMB access to the Bitbucket Server instance.

#### Configuring a Storage Bucket

You'll need to configure and select at least one migration storage bucket type when setting up your Bitbucket Server credential. [Amazon S3](amazon-s3-storage.md) and [Azure Blob Storage](azure-blob-storage.md) are currently supported.

{% include "../../../.gitbook/includes/intermediate-storage-hint.md" %}

#### Configuring SFTP Access (Linux)

If your Bitbucket Server instance is hosted on Linux, you will need to provide an SSH private key for SFTP access. This access is used to download archives from Bitbucket Server during the migration process.

This private key must not use a passphrase, and use one of the following supported ciphers:

* `aes256-ctr`
* `3des-cbc`
* `aes128-cbc`
* `aes192-cbc`
* `aes256-cbc`
* `blowfish-cbc`
* `twofish-cbc`
* `twofish192-cbc`
* `twofish128-cbc`
* `twofish256-cbc`
* `arcfour`
* `arcfour128`
* `arcfour256`
* `cast128-cbc`
* `aes128-ctr`
* `aes192-ctr`

#### Configuring SMB Access (Windows)

If your Bitbucket Server instance is hosted on Windows, you will need to provide credentials for accessing the host using SMB. This access is used to download archives from Bitbucket Server during the migration process.
