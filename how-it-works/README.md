---
description: High level overview of how cloud-concierge operates
---

# How it Works

**Form Factor:** cloud-concierge is delivered as a Docker container.

**Features**:

1\) Identify drift within resources managed by Terraform&#x20;

2\) Codify resources outside of Terraform control

3\) Identify the IAM accounts that made these changes to your cloud environment outside of your Terraform workflow.

4\) Run cost estimation and static security analysis over the Terraform files representing the current cloud environment.

**Output**: [**Link to example output.**](https://github.com/dragondrop-cloud/cloud-concierge-example/graphs/traffic) Aggregrate results and output via a Pull Request into the specified code repository.&#x20;

**Data Ingestion:** All data is stored locally in a volume attached to the cloud-concierge container. cloud-concierge ingests with read-only access to the following:

1\) A code repository of your choice

2\) A representation of the specified cloud environment respresented as Terraform

3\) Terraform remote state files.
