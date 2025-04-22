---
description: Our Commitment to Keeping Your Data Confidential
icon: vault
---

# Data Privacy

Organizations are increasingly concerned about the collection, storage, and processing of their data, and Packfiles is no exception.

Just as Packfiles maintains strong core values around security, we do the same with data privacy. Packfiles strives to ensure customers are protected by comprehensively minimizing our exposure to privileged information or administrative access to the greatest extent possible. That's why we've taken steps to ensure our products respect your organization's right to privacy and transparency in how your data is processed.

The design of Warp's [Private Compute](private-compute.md) and [Credential Management](credential-management.md) techniques guarantee that any processing of your private data (source code, commit history, credentials, and so on) occurs in an environment you own and on infrastructure you control. Combined with our strong commitments and controls around privacy and data residency, we aim to categorically mitigate risks associated with the storage and processing of your organization's information.&#x20;

### Data Residency

All infrastructure and persistent storage related to Warp's Control Plane is hosted in the eu-west-1 region of Amazon Web Services. This AWS region is geographically located in Dublin, Ireland.

[AWS Regions Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html)

### Data Privacy

The Warp Control Plane maintains an inventory of repositories and associated resources discovered in your environment to provide you with migration services. This index is used exclusively to render migration services to customers. It includes only information about the existence and location of resources in your environment, but does not store their contents.&#x20;

For example, a repository discovered in your environment as a result of a scanning process would store the name, url, and metadata (such as its size in bytes and level of activity) in the Control Plane. However, the _content_ of the repository (its source code, commit history, and so on) is never stored by Packfiles.&#x20;

Packfiles does not mine your organization's data for any purposes not outlined above or in our [Terms of Service](https://pack.fm/warp/tos) and [Privacy Policy](https://pack.fm/warp/privacy). We do not traffic in your organization's information, and will not sell or otherwise expose that data to third parties for any purpose.

### Data Security&#x20;

The Warp Control Plane uses advanced encryption techniques to ensure the security, privacy, and integrity of customer data. Information about your Project, Sources, and environment are stored securely in our Control Plane's database with row-level encryption techniques.

Packfiles maintains a dedicated team of security experts and comprehensive programs to ensure our company, our customers, and their data are protected. To learn more, review our [Security Programs Documentation](../packfiles.md#programs).

