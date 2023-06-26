---
description: Customizing the execution of cloud-concierge with environment variables
---

# Environment Variables

## Resources

* We provide [.env templates](https://github.com/dragondrop-cloud/cloud-concierge/tree/dev/examples/environments) for needed environment variables by cloud provider type
* The dragondrop management platform offers a client-side environment variable validator to quickly check whether your environment variables are formatted correctly. This can be found [here](https://app.dragondrop.cloud/env-var-validator).

### Managed Solution

Using [dragondrop.cloud](https://app.dragondrop.cloud) as a managed solution allows the management of all non-sensitive variables through a user interface.

## Variable Descriptions

### cloud-concierge Env Vars

`CLOUDCONCIERGE_ORGTOKEN`

* **Description**: Token for your dragondrop organization.
  * Sign-into the [dragondrop management platform](https://app.dragondrop.cloud) through GitHub social sign-on. You will be redirected to the "Organization" tab, where you will have the opportunity to copy your org token.
* **Example**: cco-my-org-token

`CLOUDCONCIERGE_MIGRATIONHISTORYSTORAGE`

* **Description**: Optional variable if wishing to [run CI/CD](running-imports-with-ci-cd.md) in GitHub Actions with Terraform pre-1.5.
  * At this point in time, only AWS and GCP history storages are supported.
* **Example** **GCP**: {"storageType":"Google Storage Bucket","bucket":"imports-history-exmaple","region":"us-east4"}
* **Example AWS**: {"storageType":"S3","bucket":"imports-history-exmaple","region":"us-east-1"}&#x20;

### Cost Calculation Tokens Job Env Vars

`CLOUDCONCIERGE_INFRACOSTAPITOKEN`

* **Description**: Registered Infracost API token. Can be either hosted or self hosted.
  * Docs on Infracost API token creation can be found [here](https://github.com/infracost/cloud-pricing-api).
* **Example**: my-infracost-api-token

### Terraform Env Vars

`CLOUDCONCIERGE_TERRAFORMVERSION`

* **Description**: Terraform semantic version number
* **Example**: 1.5.1

`CLOUDCONCIERGE_PROVIDERS`

* **Description**: Terraform providers semantic version numbers
* **Example**: google:\~>4.27.0,aws:\~>4.59.0

### Terraform State Backend Env Vars

`CLOUDCONCIERGE_STATEBACKEND`

* **Description**: Type of backend used to store state files.
  * Must be one of `s3`, `azurerm`, `gcs`, or  `TerraformCloud`&#x20;
* **Example**: s3

`CLOUDCONCIERGE_WORKSPACEDIRECTORIES`

* **Description**: A list of relative directories within the VCS repo cloned by cloud-concierge. Each relative directory in the list should correspond to a single "state file" of Terraform infrastructure.
  * Name comes from the idea of a "Workspace" in Terraform Cloud.
* **Example**: /my/relative/path/1/,/my/relative/path/2/

### Scanning Your Cloud Env Vars

`CLOUDCONCIERGE_DIVISIONCLOUDCREDENTIALS`

* **Description**: Mapping between the name of a division of a public cloud provider and the corresponding credential for access to your cloud environment.
  * A division for AWS is an account name, for Azure it is a resource group, and for GCP it is a project.
  * _AWS Example_: A service account credentials key map of the format {awsAccessKeyID: "", awsSecretAccessKey:""}
  * _Google Example_: A service account key with new-lines and tabs removed.
  * _Azure Example_: A service account identifying JSON dictionary
* **Structure**: "{google-divisionName1}:{serviceAccount1}"
* **Example**: my-gcp-project:{service account secret key},my-aws-account:{awsAccessKeyID": "MYKEYID","awsSecretAccessKey": "MYSECRETKEYID"},my-azure-resource-group:{"client\_id":"","client\_secret":"","tenant\_id":"","subscription\_id":""}

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

### Version Control System (VCS) Env Vars

`CLOUDCONCIERGE_VCSSYSTEM`

* **Description**: Name of the VCS system to be referenced.
  * At this point in time, only the value `github` is supported.
* **Example**: github

`CLOUDCONCIERGE_VCSBASEBRANCH`

* **Description**: Name of the base branch against which a Pull Request created by cloud-concierge should be opened.
* **Example**: main

`CLOUDCONCIERGE_VCSTOKEN`

* **Description**: Personal access token for the VCS provider specified. Allows the containerized executable to interact with the VCS provider to open a pull request containing new resources and needed migrations.
  * For GitHub, should only be provided "Repo" permissions.
* **Example**: ghp\_my-github-access-token

`CLOUDCONCIERGE_VCSUSER`

* **Description**: User ID for the user who's personal access token is being used for repo access.
* **Example**: MyTeamMember

`CLOUDCONCIERGE_VCSREPO`

* **Description**: Personal access token for the VCS provider specified. Allows the containerized executable to interact with the VCS provider to open a pull request containing new resources and needed migrations.
  * For GitHub, should only be provided "Repo" permissions.
* **Example**: ghp\_my-github-access-token

`CLOUDCONCIERGE_VCSPULLREVIEWERS`

* **Description**: VCS user name to be assigned as  Pull Request reviewer once cloud-concierge creates a pull request.
* **Example**: MyPRReviewerID

### Terraform Cloud Env Vars (if selected as your state backend)

`CLOUDCONCIERGE_TERRAFORMCLOUDTOKEN`

* **Description**: Terraform cloud team token for accessing remote workspaces.
  * Should be a Terraform Cloud Team Token.
* **Example**: my-tf-cloud-team token

`CLOUDCONCIERGE_TERRAFORMCLOUDORGANIZATION`

* **Description**: Name of the Terraform cloud organization that corresponds to the specified token.
* **Example**: my-tf-cloud-org
