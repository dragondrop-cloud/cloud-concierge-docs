---
description: The what, where and how of the cloud-concierge tool.
---

# Introduction

cloud-concierge is an OSS container that allows you to layer functionality on top of an existing Terraform workflow. Namely:

* :white\_check\_mark: Cloud Codification
* :white\_check\_mark: Drift Detection&#x20;
* :white\_check\_mark: Flag the accounts making cloud changes outside of your Terraform workflow
* :white\_check\_mark: Cloud-wide cost estimation, powered by infracost
* :white\_check\_mark: Cloud-wide security scans, powered by tfsec (checkov integration coming soon)

cloud-concierge delivers all of the following features directly as a Pull Request to a version control repository of your choice. It currently supports AWS, Azure, and GCP, and integrates with GitHub as a version control system.

### Motivation

Many teams build their own Terraform management "stacks" using major cloud provider state backends and tools like Atlantis for running `plan` and `apply` and state-locking.

For more sophisticated tooling, some may turn to tools like Terraform Cloud, Scalr, Spacelift and Firefly. We find, however, that these tool's pricing can become particularly onerous (or features simply don't exist) to allow self-hosted runners or access the most desired features like drift detection, cloud codification, security scanning, etc. for an entire cloud environment.

### Quick Start

Configure an environment variable file (using [one of our templates](https://github.com/dragondrop-cloud/cloud-concierge/tree/dev/examples/environments) to get started), and then run cloud-concierge the following command:

```bash
docker run --env-file ./my-env-file.env -v main:/main -w /main  dragondropcloud/cloud-concierge:latest
```

For more details, see [Getting Started](running-cloud-concierge/getting-started.md).

### Managed Offering

[dragondrop.cloud](https://dragondrop.cloud) provides a managed offering for configuring cloud-concierge using a user interface, coordinating scheduled executions, and visualizing results across time and multiple cloud-concierge configurations.

All usages of cloud-concierge are self-hosted, and you can try the platform out for [free today](https://app.dragondrop.cloud).
