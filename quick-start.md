---
description: Get results in < 5 minutes for either AWS, GCP, or Azure
---

# Quick Start

### All Cloud Provider Pre-requisites

1\) Configure an environment variable file (use one of our [templates](https://github.com/dragondrop-cloud/cloud-concierge/tree/dev/examples/environments/) to get started) to control the specifics of cloud-concierge's coverage.

2\) Run `docker pull dragondropcloud/cloud-concierge:latest` to pull the latest image.

### AWS

a) Run `aws config` on your CLI and ensure that credentials with read-only access to your cloud are configured. If referencing state files stored in an s3 bucket, the credentials specified should be able to read those state files as well.    &#x20;

b) Run the cloud-concierge container using the following command:

```bash
docker run --env-file ./my-env-file.env -v main:/main -v ~/.aws:/main/credentials/aws:ro -w /main  dragondropcloud/cloud-concierge:latest
```

On Windows, substitute `$HOME/.aws:` for `~/.aws:`in the above command.

c) Upon job completion, check the repository against which you configured cloud-concierge to run. There will be a new [Pull Request](how-it-works/pull-request-output.md) that has been created by Cloud Concierge.

### GCP

a) Run `gcloud auth application-default login` on your CLI and ensure that your role has read-only access to your cloud. If referencing state files stored in a GCS bucket, the selected role should be able to read those state files as well.

b.1) On MacOS/Linux, run the cloud-concierge container using the following command:

```
docker run --env-file ./my-env-file.env -v main:/main -v ~/.config/gcloud:/main/credentials/gcp:ro -w /main  dragondropcloud/cloud-concierge:latest
```

b.2) On Windows, run the cloud-concierge container using the following command:

```
docker run --env-file ./my-env-file.env -v main:/main -v $HOME/AppData/Roaming/gcloud:/main/credentials/gcp:ro -w /main  dragondropcloud/cloud-concierge:latest
```

### Azure

a) Create a service account with read-access to your cloud environment, as well as the ability to read state files in an Azure blob storage container if necessary for your cloud-concierge execution. Store credentials for this service account in the file `~/.azure/sa_credentials.json` with the following format\*:

```
{"client_id":"","client_secret":"","tenant_id":"","subscription_id":""}
```

\*We are very aware that this is not an ideal workflow, and are tracking a ticket to improve the ease of using cloud-concierge with Azure [here](https://github.com/dragondrop-cloud/cloud-concierge/issues/41).

b) Run the cloud-concierge container using the following command:

```
docker run --env-file ./my-env-file.env -v main:/main -v ~/.azure:/main/credentials/azurerm:ro -w /main  dragondropcloud/cloud-concierge:latest
```

On Windows, substitute `$HOME/.azure:` for `~/.azure:`in the above command.
