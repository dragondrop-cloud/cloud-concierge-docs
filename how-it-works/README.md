---
description: High level overview of how cloud-concierge operates
---

# How it Works

0\) cloud-concierge is a Docker container that provides Terraform Best Practices as a Pull Request.

1\) cloud-concierge clones a Version Control repository of your choice, creates a representation of your designated cloud environment subset in Terraform, and pulls down the current state of Terraform by downloading remote state files. All data is stored locally in a volume attached to the cloud-concierge container.

2\) Identify drift within resources managed by Terraform and new resources outside of Terraform control to codify.

3\) Identify the IAM accounts that made these changes to your cloud environment outside of your Terraform workflow.

4\) Run cost estimation and static security analysis over the Terraform files representing the current cloud environment state.

5\) Aggregrate results from previous steps and output via a Pull Request.
