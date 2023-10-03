# 🔓 Security

### (O) Open source by design

The entire [cloud-concierge](https://github.com/dragondrop-cloud/cloud-concierge) container code is open sourced under an Apache 2.0 license, and is available for viewing and auditing at any time

### (1) No sensitive data on your cloud posture ever leaves your existing tool set.

* The cloud-concierge container is self-hosted for all executions
* After container execution, cloud posture and codification results are exposed through a pull request within your existing VCS
* All telemetry for OSS executions and anonymized data collected from dragondrop-managed jobs can be viewed publicly on GitHub, [here](https://github.com/dragondrop-cloud/cloud-concierge/blob/dev/main/internal/implementations/dragon\_drop/http\_dragondrop\_oss\_methods.go) and [here](https://github.com/dragondrop-cloud/cloud-concierge/blob/dev/main/internal/implementations/dragon\_drop/http\_dragondrop\_managed\_visualization.go), respectfully.

### (2) cloud-concierge only requires read-only permissions for your cloud environment.

When generating roles for cloud-concierge to be able to complete the requisite cloud scanning, only read-only permissions should be granted. If accessing state files from a storage bucket, then the credentials should have read access to only that storage bucket.

### (3) Changes are recommended via Pull Request, never made directly.

The cloud-concierge container will never directly make changes to your Terraform code base. It will (via a [GitHub App](https://github.com/apps/cloud-concierge)) only open a Pull Request in your VCS containing recommended changes and import blocks/import statements.

* Like all other code, your developers have final sign-off and approval on whether to merge the suggestions.
* Comments, discussions and changes to the original cloud-concierge suggestions are all recorded within your VCS.
* All Terraform workflows are run by your existing set up, be it open-source or built off a managed offering like Terraform Cloud.
