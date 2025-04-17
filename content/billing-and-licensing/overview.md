---
description: Understand Billing and Licensing options in Warp
icon: mountain-sun
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

# Overview

At Packfiles, we're passionate about treating our customers with care and respect. Our values define everything from the core experience and overall design of Warp, to our clear and intentional approach to billing and licensing.&#x20;

We've designed Warp to provide our customers with an unprecedented level of transparency and control over their migration process. To achieve this, we've created a simple and flexible **volume pricing model** that puts customers in control. We refer to this model as **Capacity**.

### About Capacity

**Capacity** is Warp's unit of account for **successful distinct migrations**.&#x20;

Capacity is recorded in your Project's **Meter**. When you use Warp to migrate a repository from your Source environments to your destination on GitHub, you'll consume units of Capacity that are debited against your Project's Meter.

Your Project's Meter is credited with a [free trial allotment](free-tier.md) of Capacity when it's first created. Additional Capacity is credited any time you purchase one or more [**Boxes**](overview.md#about-boxes).&#x20;

Capacity purchased on behalf of your Project is available for consumption immediately after your payment is processed. Purchased Capacity associated with your Project does not expire.

### About Boxes

Capacity is sold in prepackaged bundles known as **Boxes**. Boxes provide you with flexibility and control over licensing for your Project, giving you the option to commit to adopting Warp in incremental phases, or fully up front.

You can purchase Boxes from the Capacity page of your Project at any time.

{% include "../.gitbook/includes/box-sizes-and-prices.md" %}

### Billable Events

Your Project's Meter is only debited for the repositories you choose to migrate, and you will only be billed for the first **successful, distinct** migration.&#x20;

If you migrate the same repository successfully multiple times, you'll only be billed for the first successful migration. Similarly, if you attempt to migrate a repository but are unsuccessful, you will only be billed once for the first time the migration succeeds.
