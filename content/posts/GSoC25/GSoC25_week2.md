---
title: "GSoC: Week 2"
date: 2025-06-15
description: "Diving into pattern matching behavior in git refs list, proposing a flexible design, and sending out the first RFC."
type: "post"
---

### Summary

Week 2 of GSoC 2025 was focused on refining the behavior of `git refs list`,
especially around pattern matching. While the core implementation was in place,
this week involved evaluating design decisions, adjusting tests, and initiating
broader community discussions.

### What I Worked On

After completing the initial `git refs list` implementation last week, I spent
this week exploring how pattern matching should behave.

Originally, I implemented `show-ref` style matching, assuming that's what was
expected. But during review, we explored that `for-each-ref` also supports
pattern matching, offering a more flexible and expressive design.

This sparked an important discussion: Which style should `git refs list` adopt,
`show-ref`'s for compatibility, or `for-each-ref`'s for flexibility?

I proposed:

- Defaulting to `for-each-ref` style pattern matching for its flexibility.

- Optionally supporting `show-ref`'s behavior via a flag, to preserve backward
compatibility.

My mentor agreed and suggested we take this discussion to the Git mailing list
via an RFC to get community consensus. Since the `show-ref` style was already
implemented, we decided to send that as the initial version and iterate based
on feedback.

I also extended the test suite to cover multiple pattern cases to ensure
correct behavior when several patterns are passed.

### Challenges

This week revolved more around design discussions than implementation. The main
challenge was balancing legacy compatibility with modern flexibility, and
clearly communicating those trade-offs for feedback.

### What's Next

In the coming week, I plan to:
- Review and respond to mailing list feedback.
- Update the implementation based on community suggestions.
- Continue enhancing `git refs list` with additional flags and options.

And that's a wrap! See ya' next week.
