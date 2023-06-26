---
description: Contributions, big and small, are both welcomed and encouraged!
---

# Contributing

### Table of Contents

* [Introduction](https://github.com/dragondrop-cloud/cloud-concierge/blob/dev/CONTRIBUTING.md#introduction)
* [How to contribute](https://github.com/dragondrop-cloud/cloud-concierge/blob/dev/CONTRIBUTING.md#how-to-contribute)
* [Coding conventions](https://github.com/dragondrop-cloud/cloud-concierge/blob/dev/CONTRIBUTING.md#coding-conventions)
* [Pull request](https://github.com/dragondrop-cloud/cloud-concierge/blob/dev/CONTRIBUTING.md#pull-requests)
* [Release Process](https://github.com/dragondrop-cloud/cloud-concierge/blob/dev/CONTRIBUTING.md#release-process)
* [Code of Conduct](https://github.com/dragondrop-cloud/cloud-concierge/blob/dev/CONTRIBUTING.md#code-of-conduct)
* [License](https://github.com/dragondrop-cloud/cloud-concierge/blob/dev/CONTRIBUTING.md#license)

### Introduction

This document is a guide for people who want to contribute to Cloud Concierge. All contributions, no matter how big or small, are greatly appreciated.

### How to contribute

There are many ways to contribute to Cloud Concierge, including:

* Providing feedback and requesting features
* Reporting bugs and issues (either in code or in documentation)
* Developing new features
* Fixing bugs

Before you start contributing, please read our [Code of Conduct](https://github.com/dragondrop-cloud/cloud-concierge/blob/dev/CONTRIBUTING.md#code-of-conduct).

### Coding conventions

In general, we follow the [Go Style Guide](https://google.github.io/styleguide/go/), and run [golangci](https://github.com/dragondrop-cloud/cloud-concierge/blob/dev/.golangci.yml) linting as a part of our CI/CD pipeline.

### Pull requests

When you have made changes to the codebase that you would like to contribute back, please follow these steps:

1. Search existing issues or create a new issue for the feature you are creating or the bug you are fixing. Our team will reach out and help provide feedback so that the path from Pull Request to Merge is as smooth and quick as possible. Each PR should be linked to an issue.
2. Fork the repository and create a new branch from `dev`.
3. Make changes and ensure that the code passes all tests. This can be done by navigating to `pkg` directory of the project and running `go test ./...`.
   * All new features should include unit tests for the new functionality.
   * To test your changes with an end to end execution of the container, you can run `docker-compose up --build cloud-concierge` from the root of the repository.
4. If applicable, update the [documentation](https://docs.cloudconcierge.io/) to reflect your changes, if applicable.
5. Submit a pull request to the `dev` branch.

We will review your Pull Request as soon as possible (step 0. above will help expedite this process).

### Release Process

**NOTE: We cannot guarantee that the default branch, `dev`, is stable. You should always use published releases for your production use.**

* After unit test, linter and code review requirements are met, pull requests are merged to the default `dev` branch.
* We tag and deploy a beta release image off of the updated dev branch, and run additional end-to-end tests on this branch to ensure new features do not break existing functionality.
* Once validated, we merge the `dev` branch to the `prod` branch, and tag and deploy a release image off of the `prod` branch to [DockerHub](https://hub.docker.com/r/dragondropcloud/cloud-concierge). These images should be used in production.

### Code of Conduct

We expect all contributors to follow our [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code\_of\_conduct/) when participating in our community. Please review prior to contributing.
