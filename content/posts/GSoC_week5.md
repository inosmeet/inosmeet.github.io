---
title: "GSoC: Week 5"
date: 2024-07-01
description: ""
type: "post"
---

## What did I do?

- [Database populator script](https://github.com/intel/cve-bin-tool/pull/4223)
- [Renamed database](https://github.com/intel/cve-bin-tool/pull/4225)

This week, I created a Python script that loads the `mismatch` database with the contents of the `data` directory. I also finalized a file/directory structure for this data directory:
```
└── data
    └── package_namespace
        └── product
            └── mismatch_relations.yml

For example:
└── data
    └── pypi
        └── zstandard
            └── mismatch_relations.yml
```

These `mismatch_relations` files contain mapping information for `PURLs` and `invalid_vendors`:
```yml
purls:
  pkg:pypi/zstandard
invalid_vendors:
  - facebook
```

So, this database populator script stores the mapping of PURLs and invalid vendors into the `mismatch` database.

While working on this, we iterated over the naming of the database and decided to rename it to `mismatch` from `deduplication`, so I made that change. During this process, we also discussed whether the 
`DELETE` query I was using to ensure the uniqueness of the data was efficient performance-wise. After looking into it, I figured out a more efficient way and I implemented that as well.

## What's coming up next week?

For the upcoming week, I plan to:

- Create a CI script that triggers/executes the populator script, which will load the contents of the PR into the database.
- Include a flag feature that allows data insertion for any particular subdirectory of `data`.
- Write detailed documentation on "How to fix a mismatch".
- Write initial test to check script's functionality.

This CI script will trigger when the `data` directory is modified. I'm also thinking of adding a demo PR of this to facilitate documentation.


Catch you later! More to come next week.
