---
title: "GSoC: Week 7"
date: 2024-07-15
description: ""
type: "post"
---

## What did I do?

- [test: mismatch_loader](https://github.com/intel/cve-bin-tool/pull/4248)
- [disabled failing tests](https://github.com/intel/cve-bin-tool/pull/4247)


This week, I wrote a test for our `mismatch_loader` script that verifies its functionality using a temporary database and data directory. It worked as expected in Linux but
failed on Windows. This was a hurdle, but after further investigation, I discovered that temporary files are handle defferently in Linux and Windows. Linux offers automatic 
removal of temporary files, but in Windows, we have to remove it manually.

Some of the tests have been failing for quite some time. After discussing with my mentor, I temporarily disabled them.

## What's coming up next week?

For the upcoming week, I plan to:

- yaml checks for `mismatch_relations` pull request.
- enable mismatch feature for remaining parsers.

These YAML checks will validate the `mismatch_relations.yml` file within the `data/**` directory. I’m considering creating custom rules to ensure the file contains both the
required lists: `purls` and `invalid_vendors`.

While introducing the `mismatch` database, I initially enabled its use only for the `python` parser. It's been some time now, so I think I'll enable it for the rest of the 
parsers.

Catch you later! More to come next week.
