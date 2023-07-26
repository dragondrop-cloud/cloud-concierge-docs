# Getting Started

1\) Configure an environment variable file (using [one of our templates](https://github.com/dragondrop-cloud/cloud-concierge/tree/dev/examples/environments) to get started).

2\) Make sure you have docker available on your local machine

3\) Run the cloud-concierge container using the following command:

```bash
docker run --env-file ./my-env-file.env -v main:/main -w /main  dragondropcloud/cloud-concierge:latest
```

4\) Upon job completion, check the repository that you configured to run the cloud-concierge container against. There will be a new [Pull Request](how-it-works/pull-request-output.md) that has been created by Cloud Concierge.
