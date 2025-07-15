---
title: "GSoC: Weeks 5 & 6"
date: 2025-07-13
description: "Community feedback on refs list, feature parity concerns, and next steps for deduplication."
type: "post"
---

### Summary

Weeks 5 and 6 revolved around community feedback, reevaluating our direction,
and aligning expectations for the long-term goals of consolidating Git's
ref-related commands.

### What I Worked On

At the end of Week 4, I had submitted an RFC to the Git mailing list for
consolidating `for-each-ref` under the new `git refs list` subcommand. The
initial idea was to begin with full feature parity and use this consolidation
as a stepping stone toward improving discoverability and possibly refining the
interface over time.

In the mailing list thread, I clarified that I wasn't proposing any immediate
changes or new options, just opening the door for discussion by highlighting
that having a consolidated interface could encourage future improvements. The
primary motivation remained discoverability: grouping ref-related behavior
under `git refs` rather than spreading it across top-level commands.

Junio responded with thoughtful concerns. He emphasized that while internal
unification might seem like an improvement, from a user's perspective,
`branches`, `tags`, and `symbolic refs` often feel like separate entities. He
warned that introducing subtle behavioral differences even unintentionally
could confuse users and counter Git's usability goals. His stance was clear: if
we're creating a new subcommand, we must maintain full feature parity with
`for-each-ref`, and avoid unnecessary divergence.

Patrick partially agreed. He supported keeping shared infrastructure and
consistent options but pointed out a real-world performance bottleneck in the
default output format of `for-each-ref`, which includes `%(objecttype)`, an
expensive call that hits the object database. In very large repositories like
`Chromium`, this makes a measurable performance difference. He suggested we
consider improving such defaults under `git refs list`, so long as we do it
within the shared infrastructure.

Jialuo, also chimed in with a helpful suggestion: if we want to reduce
duplication and ensure long-term maintainability, we could consider making `git
refs list` a thin wrapper over `for-each-ref`. This approach could help us
minimize redundancy while preserving exact behavior. Since this idea is still
under discussion, I plan to hold off on implementing anything until the
community reaches a consensus.

In our weekly meeting, we also discussed one of the more practical next steps:
refactoring and deduplicating option parsing logic shared between
`for-each-ref` and `refs list`. As things stand, the option definitions are
redundantly specified.

### Challenges

The biggest challenge in this phase was aligning technical goals with community
expectations. The shift from "feature parity now, improvements later" to
"feature parity is mandatory" added clarity, but also narrowed the scope for
iteration. At the same time, it raised important questions around performance,
defaults, and long-term maintainability.

### What's Next

In the coming weeks, I plan to:

- Follow up on any remaining mailing list discussion.
- Begin work on shared option parsing infrastructure.
- Prepare for any adjustments to `refs list` once the community direction
settles fully.

Until next time!
