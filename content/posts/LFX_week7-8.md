---
title: "LFX: Week 7-8"
date: 2025-04-28
description: ""
type: "post"
---

- [Add tests for sample APIs](https://github.com/microcks/microcks/pull/1577)
- [Cover helm in check-health script](https://github.com/microcks/microcks/pull/1580)
- [Add websocket test for sample-async api](https://github.com/microcks/microcks/pull/1589)

During weeks 7 and 8, I introduced tests for our sample APIs covering `gRPC API`, `REST HelloAPI`,
and the `Petstore API`. By simulating realistic payloads, status codes, and error conditions, these
tests have been integrated into the api-tests script.

Next, I added Helm-related support to the check-health script to bring parity across deployment
methods. We now support healthcheck testing for `docker-compose`, `podman-compose`, and `helm`
deployments.

Finally, I added a WebSocket test for our sample-async API using `asyncAPI mocks`. This test
verifies the HTTP 101 handshake, collects messages over a defined interval, and asserts key
events—such as User Signed-Up—to ensure our event-driven samples remain stable. With this addition,
our tests now cover all sample APIs.

Over the next two weeks, I will be focusing primarily on my end-semester exams. While my study
schedule will take priority, I will continue to address low-priority project tasks and incorporate
any quick fixes or feedback as time permits.


For the upcoming weeks, I plan to

- Create a GitHub Actions workflow for sample API tests, decoupled from benchmarking jobs.
- Expand documentation (initiated [here](https://github.com/microcks/microcks/blob/1.12.x/testsuite/README.md))
- Extend tests to cover `Microcks'` own APIs.
- Investigate and remediate intermittent timing issues observed in parallel healthcheck runs.
- Address feedback from code reviews.


Off to hit the books—next report lands in a month!
