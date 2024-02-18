---
description: The what, where and how of the cloud-concierge tool.
---

# Introduction

[cloud-concierge is an OSS container](https://github.com/dragondrop-cloud/cloud-concierge) that allows you to layer functionality on top of an existing Terraform workflow. Namely:

* :white\_check\_mark: Cloud Codification
* :white\_check\_mark: Drift Detection&#x20;
* :white\_check\_mark: Flag the accounts making cloud changes outside of your Terraform workflow
* :white\_check\_mark: Cloud-wide cost estimation, powered by infracost
* :white\_check\_mark: Cloud-wide security scans, powered by tfsec (checkov integration coming soon)

cloud-concierge delivers all of these features directly as a Pull Request to a version control repository of your choice. It currently supports AWS, Azure, and GCP, and integrates with GitHub as a version control system.

### Motivation

Many teams build their own Terraform management "stacks" using major cloud provider state backends and tools like Atlantis for running `plan` and `apply` and state-locking.

For more sophisticated tooling, some may turn to tools like Terraform Cloud, Scalr, Spacelift and Firefly. We find, however, that these tool's pricing can become particularly onerous (or features simply don't exist) to allow self-hosted runners or access the most desired features like drift detection, cloud codification, security scanning, etc. for an entire cloud environment.

### [Quick Start](quick-start.md)

Get started locally in minutes!
