---
icon: building-lock
description: Learn about Warp's Secure Design
---

# Warp's Security Model

Much has been said about "Zero-Trust" security architecture, but in practice, few vendors are able to truly deliver on that vision. Doing so requires a deep commitment to protecting the security and confidentiality of customer data, along with the drive and technical skill needed to solve the host of engineering challenges that make it possible to deliver scalable, resilient systems with these properties.&#x20;

When we originally set out to design Warp, we were met with the following security challenges:

* Most migration tools, including first-party tools published by GitHub, require a combination of many highly privileged credentials to perform their work.
* Any individual operating migration tools, whether for their own use or on behalf of another organization, is required to have the privileged credentials mentioned previously to carry out migration tasks.&#x20;
  * Due to the privileged nature of these credentials, the number of these individuals is typically small, further constraining the throughput of the migration process.
* Because migrations necessarily involve the processing of nearly all an organization's software artifacts, including those of a business-critical or trade-secret nature, customers require the utmost transparency, security, and governance of these processes.

Based on these challenges, we identified the following key problems to solve:

* Storing and managing credentials securely,&#x20;
* Executing migration tools without exposing credentials or compromising the integrity of the runtime environment, and&#x20;
* Ensuring the confidentiality, integrity, and privacy of customer data.

### Credential Management&#x20;

To solve the problem of securing the management and storage of credentials, Warp's **Vault** protects your key material with end-to-end encryption.

**When you use Warp, your credentials, along with the key used to encrypt the Vault that contains them, are never known to Packfiles.** Your key material is encrypted and maintained exclusively in your GitHub environment, on infrastructure you control, and is never stored or processed on Packfiles' infrastructure or in a form accessible by our staff.

To learn more about the Vault, have a look at the [Credential Management](credential-management.md) section.

### Private Compute

To execute migration tools and processes securely, while also placing control in the hands of our customers, we designed the [Warp Runner Agent](../../using-warp/migration-hq/runner-agent.md).&#x20;

When you use Warp to invoke any process that operates on your source environment, it's carried out by the Warp Runner Agent. **The Warp Runner Agent executes exclusively in your environment, on infrastructure you own and control.**

The Warp Runner Agent is the only component of Warp responsible for invoking migration tools and connecting to your source environment. To learn about the security properties of its design, check out the [Private Compute](warp-security-model.md) section.

### Data Privacy&#x20;

We've taken strong and intentional steps to ensure the confidentiality and privacy of our customers' data. Review the [Data Privacy](./#data-privacy) section to learn about our commitments and safeguards.
