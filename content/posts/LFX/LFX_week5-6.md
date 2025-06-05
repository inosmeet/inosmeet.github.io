---
title: "LFX: Week 5-6"
date: 2025-04-14
description: ""
type: "post"
---

- [Add workflow for testing sample APIs](https://github.com/microcks/microcks/pull/1544)
- [Add workflow file for healthchecks](https://github.com/microcks/microcks/pull/1564)
- [Add installation script for microcks](https://github.com/microcks/microcks/pull/1567)
- [Add config for healthcheck workflow](https://github.com/microcks/microcks/pull/1570)
- [Modify check-health script to cover helm installation](https://github.com/microcks/microcks/pull/1574)

During these two weeks, I focused on enhancing `Microcks'` CI workflows and healthcheck automation
across multiple installation methods. I revisited the PR for testing sample APIs, which had been on
hold pending config decisions. With the approach now finalized, I updated the PR to centralize the
API testing logic so it can be reused by both our benchmark suite and the upcoming dedicated
workflow.

In parallel, I created a new GitHub Actions workflow to handle healthchecks for the `docker-compose`
installation method. To support this, I introduced an installation script that simplifies deploying
various `Microcks` flavors. I then expanded the healthcheck logic further to support
`podman-compose` and `helm` based installations via dedicated PRs. Together, these improvements make
our CI more robust and ensure consistent validation of Microcks deployments across different
environments.

With these updates, phase one of my `LFX` project is almost complete. The core workflows and scripts
are in place, and the only remaining task is to add a couple more configurations to the existing
setup to make it fully adaptable. Once that's done, we'll have a solid foundation for reliable and
automated testing across all supported `Microcks` installation methods.


For the upcoming weeks, I plan to:

- Expand `api-tests` script to test additional sample API endpoints.
- Address feedback from code reviews.


Done and dusted — next week, we keep building!
