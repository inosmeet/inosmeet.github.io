---
title: "LFX: Week 3-4"
date: 2025-03-31
description: ""
type: "post"
---

- [Add healthchecks for Docker-compose](https://github.com/microcks/microcks/pull/1533)
- [Add healthchecks for Podman-compose](https://github.com/microcks/microcks/pull/1551)
- [Add installation script for helm](https://github.com/microcks/microcks/pull/1546)
- [Add installation script for Docker & Podman compose](https://github.com/microcks/microcks/pull/1552)

Over these two weeks, I focused on adding healthchecks to all installation methods. My efforts
included finalizing the `docker-compose` method by addressing review comments and implementing
healthchecks for `podman-compose`.

I also added installation scripts for `helm`, `docker-compose`, and `podman-compose`. The script now
accommodates all available add-ons (via the `--addons` flag) as well as modes like `devmode` and `proxy`
(via the `--mode` flag). Since the `docker-compose` and `podman-compose` commands are interchangeable, I
merged their installation scripts, allowing users to install `Microcks` using either method via the
`--method` flag.

Over these two weeks, my goal was to expand the `k6` script to include additional API endpoints.
However, debugging became a major challenge and consumed so much of my time that I couldn’t complete
the expansion. During the debugging process, we discovered that the issue was due to a regression in
`docker-compose` with `async minion`—a problem directly related to my project. With the help of my
mentor, Laurent, we successfully resolved the regression.


For the upcoming weeks, I plan to:

- Add a CI script that ensures health of various utilized services.
- Expand k6 script to test additional API endpoints.
- Determine the optimal configuration and its relation to k6.
- Figure out how to intelligently trigger API endpoints based on the configuration.
- Address feedback from code reviews.


Catch you later! More to come next weeks.
