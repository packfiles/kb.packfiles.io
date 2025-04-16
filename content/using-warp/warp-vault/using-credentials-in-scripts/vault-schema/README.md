---
icon: brackets-curly
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

# Vault Schema

Under the hood, Warp Vault stores credentials in a versioned schema format, so they're easy to work with in scripts.

When you configure credentials in Warp Vault's graphical interface, they're stored as JSON in an encrypted container. To access these credentials in scripts, you can use Warp Vault's [Query Interface](../) to locate and extract properties of you credentials based on their schema.&#x20;

This section provides schema references for each of Warp Vault's supported credential types to help you write [VaultQL queries](../) to extract any properties you might need in scripts or other parts of your workflow.
