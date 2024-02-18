---
description: Customizing the execution of cloud-concierge with environment variables
---

# Environment Variables

## Resources

* We provide [.env templates](https://github.com/dragondrop-cloud/cloud-concierge/tree/dev/examples/environments) for needed environment variables by cloud provider type
* The dragondrop management platform offers a client-side environment variable validator to quickly check whether your environment variables are formatted correctly. This can be found [here](https://app.dragondrop.cloud/env-var-validator).

## Variable Descriptions

### cloud-concierge Env Vars

`CLOUDCONCIERGE_MIGRATIONHISTORYSTORAGE` - OPTIONAL

* **Description**: Optional variable if wishing to [run CI/CD](running-imports-with-ci-cd.md) in GitHub Actions with Terraform pre-1.5. We strongly recommend running cloud-concierge with at least version 1.5.0 of Terraform to take advantage of [import blocks](https://dragondrop.cloud/2023/06/13/terraform-1-5-xs-import-block/).
  * At this point in time, only AWS and GCP history storages are supported.
* **Example** **GCP**: {"storageType":"Google Storage Bucket","bucket":"imports-history-exmaple","region":"us-east4"}
* **Example AWS**: {"storageType":"S3","bucket":"imports-history-exmaple","region":"us-east-1"}&#x20;

### Terraform Env Vars

`CLOUDCONCIERGE_TERRAFORMVERSION`

* **Description**: Terraform semantic version number. We strongly recommend running cloud-concierge with at least version 1.5.0 of Terraform to take advantage of [import blocks](https://dragondrop.cloud/2023/06/13/terraform-1-5-xs-import-block/).
* **Example**: 1.5.1

`CLOUDCONCIERGE_PROVIDER`

* **Description**: A Terraform provider with a semantic version to use within the cloud-concierge execution.
* **Example**: google:\~>4.27.0

`CLOUDCONCIERGE_REGIONS`

* **Description**: A region of a major cloud provider to scan. Currently only one region can be scanned at a time.
* **Example**: \["eastus"]

### Terraform State Backend Env Vars

`CLOUDCONCIERGE_STATEBACKEND`

* **Description**: Type of backend used to store state files.
  * Must be one of `s3`, `azurerm`, `gcs`, or  `TerraformCloud`&#x20;
* **Example**: s3

`CLOUDCONCIERGE_WORKSPACEDIRECTORIES`

* **Description**: A list of relative directories within the VCS repo to be cloned by cloud-concierge. Each relative directory in the list should correspond to a single "state file" of Terraform infrastructure.
  * Name comes from the idea of a "Workspace" in Terraform Cloud.
* **Example**: /my/relative/path/1/,/my/relative/path/2/

### Scanning Your Cloud Env Vars

`CLOUDCONCIERGE_DIVISION`

* **Description**: Name of a division of a public cloud provider and the corresponding credential for access to your cloud environment.
  * A division for AWS is an account name, for Azure it is a resource group, and for GCP it is a project.
* **Structure**: "my-aws-account-name"

`CLOUDCONCIERGE_RESOURCESWHITELIST`

* **Description**: List of terraform resources to exclusively scan for within your cloud environment.
  * Should not be specified if `CLOUDCONCIERGE_RESOURCESBLACKLIST` is specified
* **Structure**: \["tf\_resource\_1", "tf\_resource\_2"]
* **Example**: \["aws\_lb", "google\_storage\_bucket"]

`CLOUDCONCIERGE_RESOURCESBLACKLIST`

* **Description**: List of terraform resources to avoid scanning for within your cloud environment. Scans for all other supported resources not specified
  * Should not be specified if `CLOUDCONCIERGE_RESOURCESWHITELIST` is specified.
* **Structure**: \["tf\_resource\_1", "tf\_resource\_2"]
* **Example**: \["aws\_lb", "google\_storage\_bucket"]

`CLOUDCONCIERGE_ISMANAGEDDRIFTONLY` - Optional

* **Description**: Optional boolean variable for whether cloud-concierge should only identify drift for resources already managed by Terraform.
  * Defaults to False
* **Example**: False

### Version Control System (VCS) Env Vars

`CLOUDCONCIERGE_VCSREPO`

* **Description**: Repository for which cloud-concierge against which cloud-concierge should open a pull request.
  * Currently only GitHub repositories are supported.
* **Example**: [https://github.com/dragondrop-cloud/cloud-concierge.git](https://github.com/dragondrop-cloud/dragondrop-cloud.git)

`CLOUDCONCIERGE_VCSPAT`

* **Description**: Personal access token for the VCS provider specified. Allows the containerized executable to interact with the VCS provider to open a pull request containing new resources and needed migrations. The cloud-concierge [GitHub app](https://github.com/apps/cloud-concierge) should be installed on the repo specified.
  * For GitHub, should only be provided "Repo" permissions.
* **Example**: ghp\_my-github-access-token

`CLOUDCONCIERGE_VCSPULLREVIEWERS`

* **Description**: VCS user name to be assigned as  Pull Request reviewer once cloud-concierge creates a pull request. To have no assigned reviewer, specify "NoReviewer".
* **Example**: MyPRReviewerID

### Cost Estimation Env Vars

`CLOUDCONCIERGE_INFRACOSTTOKEN`

* **Description**: Token for accessing the Infracost Cloud Pricing API.
  * You can sign up for your free token at Infracost.io
*   **Example**:&#x20;

    ```
    ico-mytoken
    ```

### Terraform Cloud Env Vars (Required if selected as your state backend)

`CLOUDCONCIERGE_TERRAFORMCLOUDTOKEN`

* **Description**: Terraform cloud team token for accessing remote workspaces.
  * Should be a Terraform Cloud Team Token.
* **Example**: my-tf-cloud-team token

`CLOUDCONCIERGE_TERRAFORMCLOUDORGANIZATION`

* **Description**: Name of the Terraform cloud organization that corresponds to the specified token.
* **Example**: my-tf-cloud-org
