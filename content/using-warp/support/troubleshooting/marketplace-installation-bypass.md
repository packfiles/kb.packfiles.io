---
description: Resolve Silent Failures During GitHub Marketplace Installation
icon: store
---

# Marketplace Installation Bypass

In rare cases, installing Warp through the GitHub Marketplace may appear to succeed, but the app is never actually installed. This happens when the webhook GitHub sends to Packfiles is not delivered, meaning the installation signal is never received.

## Symptoms

* GitHub Marketplace shows Warp as purchased or subscribed.
* No Migration HQ repository is created in your organization.
* Warp does not appear under your organization's installed GitHub Apps.

## Cause

GitHub Marketplace relies on webhooks to notify application providers when a new installation occurs. In rare cases, this webhook is not delivered. The purchase is recorded on GitHub's side, but Packfiles never receives the installation event, so the Warp GitHub App is never installed on your organization.

## Resolution

Use the direct installation link to install the Warp GitHub App, bypassing the Marketplace webhook:

1. Navigate to the direct installation URL:\
   [`https://github.com/apps/packfiles-warp/installations/new`](https://github.com/apps/packfiles-warp/installations/new)
2. Select the GitHub organization where you want to install Warp.
3. Authorize the installation and grant the required permissions.
4. Warp will begin its setup process and create the Migration HQ repository.

{% hint style="info" %}
This direct installation link can also be used if you prefer to install the Warp GitHub App without using the Marketplace.
{% endhint %}

## Verifying the Installation

After using the direct installation link, confirm that the installation succeeded:

* Check that the Migration HQ repository was created in your target organization.
* Verify that **packfiles-warp** appears under **Organization Settings** > **Installed GitHub Apps**.

## Related Pages

* [Troubleshooting](README.md) — index of all common issues
* [Support](../README.md) — contact Product Support if the direct installation link also fails
