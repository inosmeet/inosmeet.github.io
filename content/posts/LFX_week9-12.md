---
title: "LFX: Week 9-12"
date: 2025-06-02
description: ""
type: "post"
---

- [Add tests for microcks' own apis in k6 script](https://github.com/microcks/microcks/pull/1599)
- [Enable health-checks for helm in workflow](https://github.com/microcks/microcks/pull/1617)
- [Add workflow for testing APIs](https://github.com/microcks/microcks/pull/1624)

Over the past few weeks, I extended our `K6` testing suite to cover `Microcks'` own APIs. These
include key endpoints like `authentication`, `/api/features/config`, `/api/keycloak/config`,
`/api/services`, and `/api/jobs`. The tests now verify behavior both with and without authentication
to ensure consistent behavior across access levels.

Next, I wired up `helm` healthchecks into our GitHub Actions CI workflow. Although the script was
already Helm-compatible, this integration ensures that Helm-based installations are now validated as
part of the standard workflow, just like `Docker` and `Podman` setups.

I also added a dedicated workflow that runs the API tests via K6. This includes tests for both
`sample APIs` and `Microcks' APIs`, across four deployment flavors: `uber`, `uber-native`,
`regular-auth`, and `regular-noauth`. One of the trickier parts here was assigning appropriate
scopes to the test user, especially for `regular-auth`, where we needed permission to upload
artifacts. Thanks to guidance from Laurent, that was sorted. Another challenge was that K6 only
exits with an error on `script-level` failures, not on failed checks. To make our CI meaningful, I
implemented a workaround that ensures we fail builds properly when tests fail. Lastly, debugging K6
in CI was quite painful, so I added some helpful debug logs that print on failure to make life
easier.


And that wraps up my final weekly update for LFX! I’ll be back soon with one last post to reflect on
the full journey, share highlights, and say a proper goodbye. Thanks for following along!
