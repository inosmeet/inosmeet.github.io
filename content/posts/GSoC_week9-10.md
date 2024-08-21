---
title: "GSoC: Week 9-10"
date: 2024-08-05
description: ""
type: "post"
---

## What did I do?

- [test: purl2cpe database](https://github.com/intel/cve-bin-tool/pull/4280)
- [Issue template](https://github.com/intel/cve-bin-tool/pull/4283)
- [Refactor](https://github.com/intel/cve-bin-tool/pull/4292)


In the past two weeks, I wrote a test for the `purl2cpe` database that downloads the database and tests its contents for both the local cache and the CI pipeline. I also 
created an issue template to help users report bugs related to false positives or mismatches. This template guides users on how to resolve issues by adding a mismatch entry
to the database. Additionally, I refactored some repetitive code within the language parsers into a generic function.

I spent the majority of this time researching the requirements for the mismatch database as a standalone entity. I have finalized the CLI approach, where I will convert the
database into a standalone CLI feature.


## What's coming up next week?

For the upcoming week, I plan to:

- Convert mismatch into a standalone cli utility.
- Test: mismatch cli utility.
- Docs: mismatch cli utility.
- work on the reviews and issues assigned.

Catch you later! More to come next week.
