---
description: >-
  How to update Terraform state to manage newly created resources from
  cloud-concierge.
---

# Running Imports with CI/CD

## Terraform post-1.5.0

We strongly recommend running cloud-concierge with Terraform 1.5 specified.

In this case, cloud-concierge writes import statements using [Terraform 1.5+'s native import block](https://medium.com/@hello\_9187/terraform-1-5-xs-new-import-block-b8607c51287f), and allowing you to use your existing Terraform CI/CD deployment pipeline to run resource imports.

## Terraform pre-1.5.0

If the Terraform version is specified to be less than version 1.5, then cloud-concierge outputs a series of import statements corresponding to each identified resource that is outside of Terraform control. These can be run manually on the CLI, or our [Github action ](https://github.com/dragondrop-cloud/github-action-tfstate-migration)allows for a programatic `plan` and `apply` workflow of the generated import statements.
