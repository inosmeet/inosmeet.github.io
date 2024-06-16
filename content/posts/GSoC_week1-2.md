---
title: "GSoC: Week 1-2"
date: 2024-06-10
description: ""
type: "post"
---

## Agenda for the First Two Weeks:

The primary goal for the first two weeks was to introduce the `purl2cpe` database as a new data source in the codebase and propose its structure and functionality for future improvements.

## What did I do?

- [purl2cpe data source integration](https://github.com/intel/cve-bin-tool/pull/4179)
- [purl2cpe utilization](https://github.com/intel/cve-bin-tool/pull/4164)

Due to my end-semester exams, I had limited time for code contributions during the first week. So instead, I focused on researching purl requirements, determining the layer on which they should operate, and
conducting manual queries on the database locally. This helped me identify effective query types for various language parsers.

Afterward, I developed a new function to replace the current `find_vendor()` function, which occasionally causes name collisions (a key issue this GSoC project aims to address). For simplicity, I initially
developed the function to facilitate only the `Python` parser and designed the required `SQL` query accordingly. This new function leverages the `purl2cpe` database and helps mitigate name collisions as a
standalone feature.

As a result, I was able to resolve [Docutils name collision](https://github.com/intel/cve-bin-tool/issues/3152) with this.


## What's coming up next week?

For the upcoming week, I plan to:

- Accommodate all the remaining language parsers with the purl2cpe database.
- Write tests for the new data source.

## Did you get stuck anywhere?

Initially, I struggled with some misconceptions due to the lack of documentation on "How to add a data source." Unlike other data sources, the one I'm working with doesn't require further modification, 
which added to the confusion.

And that's a wrap! See ya' next week.
