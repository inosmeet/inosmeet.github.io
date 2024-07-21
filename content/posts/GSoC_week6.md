---
title: "GSoC: Week 6"
date: 2024-07-08
description: ""
type: "post"
---

## What did I do?

- [ci script](https://github.com/intel/cve-bin-tool/pull/4236)
- [flag feature](https://github.com/intel/cve-bin-tool/pull/4246)
- [demo pull request template](https://github.com/intel/cve-bin-tool/pull/4239)
- [docs](https://github.com/intel/cve-bin-tool/pull/4245)


This week, I created a CI script that adds data to the `mismatch` database whenever a pull request updates a particular directory. Additionally, I wrote documentation on the
steps for adding data to the mismatch database and a demo pull request that explains how to contribute to it.

I have introduced a `flag` feature that allows users to use their own database as well as their own data directory.

I had planned to write tests for the `mismatch` database this week, but some of the tests were failing due to a faulty cache and some unresolved bugs. As a result, I wasn't
able to complete this task. I'll be working on it in the upcoming week.

## What's coming up next week?

For the upcoming week, I plan to:

- Write initial test to check script's functionality.
- Tests for purl2cpe database.
- Work on reviews.


Signing off for now! Catch ya' next week ;)
