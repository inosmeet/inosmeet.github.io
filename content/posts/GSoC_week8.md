---
title: "GSoC: Week 8"
date: 2024-07-22
description: ""
type: "post"
---

## What did I do?

- [YAML checks](https://github.com/intel/cve-bin-tool/pull/4264)
- [enable mismatch](https://github.com/intel/cve-bin-tool/pull/4269)
- [refactor: decode_cpe23](https://github.com/intel/cve-bin-tool/pull/4268)


This week, I wrote a ci script that validates `YAML` files named `mismatch_relations.yml` within `data/**` directory that has been created/updated in latest commit. I've also made a set of custom rules to
enforce our required checks. This script passes only when the `mismatch_relations.yml` file contains two lists named exactly: `purls` and `invalid_vendors`.

`decode_cpe23` function I've been using in the parsers was basically copied temporarily from our `sbom_manager`, now I've moved it to `utils` within our project. Also, I enabled mismatch functionality 
for the remaining of the parsers.

## What's coming up next week?

For the upcoming week, I plan to:

- Write test for `purl2cpe` data source.
- Make a template for issue/pull request of mismatch information.
- Figure out how to convert `mismatch` database into a standalone library.


Signing off for now! Catch ya' next week ;)
