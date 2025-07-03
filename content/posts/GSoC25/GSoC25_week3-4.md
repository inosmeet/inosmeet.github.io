---
title: "GSoC: Weeks 3 & 4"
date: 2025-06-29
description: "Dropping show-ref, consolidating for-each-ref, and prepping for feedback."
type: "post"
---

### Summary

Weeks 3 and 4 were about shifting focus, consolidating features, and laying the
groundwork for discussions on the future of `git refs list`.

### What I Worked On

Week 2 ended with an open question: Should `git refs list` use pattern matching
behavior from `show-ref`, `for-each-ref`, or support both?

As per my mentor's suggestion, I sent an RFC to the Git mailing list. Junio
responded, pointing out that `show-ref`'s only unique value `--verify` is
already handled well by `rev-parse`. This prompted us to drop `show-ref`
consolidation altogether and shift focus to `for-each-ref`.

Over the last two weeks, I consolidated the `for-each-ref` command into `git
refs list`, carrying over its options and flags as-is. Since my project also
includes identifying unneeded features and potential improvements, I asked my
mentors whether we should modify anything up front. Their advice was to first
ensure full feature parity with `for-each-ref`, send an RFC, and discuss
changes with the broader community later.

For testing, I ran into an interesting problem. `for-each-ref` already has an
extensive test suite with 400+ tests. Duplicating all of those with a new
command name would be wasteful and hard to maintain. So instead, we decided to
reuse the existing `t/t6300-for-each-ref.sh` tests inside a new test file
(`t/t1461-refs-list.sh`) by overriding the `GIT_REFS_LIST_CMD` variable to run
tests against `git refs list`.

For documentation, I temporarily reused parts of `for-each-ref`'s doc file.
Since the command's behavior isn't finalized yet, this makes it easier to keep
docs in sync. Once the command's final design is agreed upon, I plan to revisit
the docs to better reflect what `git refs list` actually does.

### Challenges

The biggest challenge in this cycle was the sudden change of direction:
dropping `show-ref` after it was already implemented. It also took time and
care to ensure we kept the project aligned with upstream expectations and
community feedback.

### What's Next

In the coming weeks, I plan to:

- Follow up on mailing list feedback.
- Make necessary adjustments to the code and tests based on the feedback.
- Start exploring small usability improvements if the scope allows.

Most importantly, the consensus we reach on how to shape `git refs list` will
likely influence how we approach consolidating the rest of the ref-related
commands. So, next week will probably involve minor code changes but major
community discussion and alignment on direction.

Till the next check-in;)
