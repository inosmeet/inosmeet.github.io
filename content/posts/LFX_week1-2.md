---
title: "LFX: Week 1-2"
date: 2025-03-17
description: ""
type: "post"
---

## Agenda for the First Two Weeks:

The primary goal for the first two weeks was to explore the documentation, understand the `Microcks` architecture, define the testing scope for the LFX term, and work on Proof of Concept (PoC) Pull Requests
to outline the proposed testing approach.

## What did I do?

- [Add healthchecks for Docker-compose](https://github.com/microcks/microcks/pull/1533)
- [Add workflow for testing sample APIs](https://github.com/microcks/microcks/pull/1544)
- [Report/resolve some broken links](https://github.com/microcks/microcks/pull/1531)
- [More broken links](https://github.com/microcks/microcks.io/issues/376)

One of the key deliverables of my project is to verify that `Microcks` installs correctly. To achieve this, I first explored different testing approaches. After some research, I decided to add health
checks to the various services in the `docker-compose` file. These health checks ensure that each service is running as expected. Since this is a Proof of Concept (PoC) PR, the goal is to validate this
approach before fully integrating it.

Ensuring that various APIs function correctly is crucial for any software service. As part of my project, I need to determine an effective way to test these APIs across different configurations. To explore
this, I created a draft PR proposing a potential approach using [k6](https://k6.io/), a performance testing tool for APIs. So far, I have integrated tests for `Movie API: Graph`, `Pastry API v2.0: REST`,
and `Hello Service Mock API: SOAP`, with plans to expand coverage further.

While going through the documentation, I came across some broken links and submitted a PR to fix them.

## What's coming up next week?

For the upcoming weeks, I plan to:

- Explore ways to generalize installation testing.
- Expand healthchecks to cover additional installation methods.
- Expand k6 script to test additional API endpoints.
- Work on reviews.


And that's a wrap! See you in two weeks.
