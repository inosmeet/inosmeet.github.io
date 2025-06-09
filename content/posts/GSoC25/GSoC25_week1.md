---
title: "GSoC: Week 1"
date: 2025-06-08
description: "Kicking off GSoC 2025 with Git: implementing the first subcommand, 'git refs list'."
type: "post"
---

### Summary

This week, I began my journey contributing to Git as part of GSoC
2025. My project focuses on consolidating Git's ref-related functionality into
a new, unified command called `git refs`. Currently, this functionality is
scattered across multiple commands (like `git show-ref`, `git for-each-ref`,
etc.), and the goal is to create a modern interface under a single
command family.

### What I Worked On

I implemented the first subcommand: `git refs list`. This serves as a modern
replacement for `git show-ref`, currently providing the core functionality and
laying the groundwork for a more modular and coherent design.

Key tasks this week:
- Implemented the `list` subcommand inside the `builtin/refs.c` file.
- Supported an initial set of key flags from `git show-ref` for backward
  compatibility.
- Ensured the output format matches the existing command for consistency.
- Added new tests to cover the implemented functionality.

### Supported Flags and Arguments

As a first step, the `git refs list` subcommand currently supports some key
flags from `git show-ref` for backward compatibility:

- `--heads`
- `--branches`
- `--tags`

Additionally, it supports **ref patterns** as positional arguments, allowing
filtering refs by matching patterns (e.g., `git show-ref refs/heads/master`).

More flags and options will be gradually integrated to cover the full
functionality of `git show-ref`.

### Challenges

Since I had already completed much of the groundwork while writing my proposal,
this week mainly involved refining the implementation and adding pattern
matching functionality as requested by my mentor. As a result, I didn't
encounter any major roadblocks or get really stuck.

### What’s Next

In the coming week, I plan to:
- Address any feedback from mentors.
- Hopefully send the patch to the mailing list after refinements and approval
  from mentors.
- Continue working on `git refs list` by adding support for the remaining flags
  and options from `git show-ref`.

Signing off for now! Catch ya’ next week ;)
