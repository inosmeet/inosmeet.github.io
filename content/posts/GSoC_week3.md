
---
title: "GSoC: Week 3"
date: 2024-06-17
description: ""
type: "post"
---

## Agenda for the Week:

I had planned to modify all the remaining language parsers according to the requirements of the `purl2cpe` database and write tests for the `purl2cpe` data source.

## What did I do?

- [Update language parsers and query](https://github.com/intel/cve-bin-tool/pull/4188)

Updating the language parsers took more time than I anticipated. The initial approach I had taken proved to be variable across different parsers, making my query ambiguous. Midway through, I decided to 
change my approach and create a universal and dynamic query that can be generalized for every parser. This way, I could ensure all parsers follow the purl specification, making them useful in 'SBOMs' or
any other part of our codebase.


Some languages have concept of `namespace` in their purl:
```
pkg:golang/github.com/mikel/mail
```
While others do not:
```
pkg:pypi/docutils
```

The query according to the initial approach did not address this properly:
```py
query = "SELECT cpe from purl2cpe WHERE purl=?"
```

The final approach takes this into account and yields the required result:
```py
param1 = f"pkg:{type}/{product}"
param2 = f"pkg:{type}/%/{product}"

query = """
    SELECT cpe from purl2cpe WHERE purl LIKE ?
    UNION
    SELECT cpe from purl2cpe WHERE purl LIKE ?
"""
```

This lets us achieve the desired result without having to change individual parsers or use multiple/nested queries.

## What's coming up next week?

For the upcoming week, I plan to:

- Create initial schema for de-duplication database.
- Integrate it in current workflow and ensure it works as expected

Proposed schema:
```sql
CREATE table deduplication {
  purl TEXT NOT NULL,
  invalid_vendor_list TEXT[],
  PRIMARY_KEY(purl),
}
```

## Did you get stuck anywhere?

After modifying some of the parsers, I found ambiguity in the query I had curated, which required a change in approach and took more time than I expected. Apart from this, the week went quite smoothly.


Signing off for now! Catch ya' next week ;)
