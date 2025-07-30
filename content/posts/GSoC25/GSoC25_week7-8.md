---
title: "GSoC: Weeks 7 & 8"
date: 2025-07-27
description: "Simplifying refs list by wrapping for-each-ref and unifying code, docs, and tests."
type: "post"
---

### Summary

Weeks 7 and 8 focused on eliminating duplication across implementation,
documentation, and tests by restructuring `refs list` as a wrapper around
`for-each-ref`.

### What I Worked On

These two weeks were shaped by ongoing discussions with the Git community
around the direction of `refs list` and how closely it should match
`for-each-ref`. Based on the feedback, I focused on ensuring behavior and
feature parity between the two. I also worked on reducing code duplication,
particularly around formatting and filtering logic, to make way for a clean
transition.

Initially, the `refs list` command had its own implementation for option
parsing, mimicking that of `for-each-ref`. However, this introduced code
duplication and created a risk of divergence between the two commands over
time. Taking Junio's suggestion, I restructured `refs list` to act as a thin
wrapper over `for-each-ref`, similar to how `git-annotate` wraps around
`git-blame`.

The documentation also had redundant content between the two. To address this,
I extracted the common options into a shared `AsciiDoc` file
(`refs-list-options.adoc`) and used the `include::` directive in both man pages
to embed it.

As for the tests, I had initially used a variable-based approach to reuse tests
across the two commands. While this avoided duplication, it depended on shared
test libraries being idempotent, which is not guaranteed. To solve this, we
followed the structure used by `git-blame` and `git-annotate`: we moved the
common test cases to a separate file (`for-each-ref-tests.sh`) and sourced it
from both `for-each-ref` and `refs list` test scripts.

### What's Next

In the coming weeks, I plan to:

- Follow up on any remaining mailing list discussion.
- Begin exploring other ref-related commands for consolidation

Back to coding, see you in the next update!
