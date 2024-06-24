---
title: "GSoC: Week 4"
date: 2024-06-24
description: ""
type: "post"
---

## What did I do?

- [de-duplication](https://github.com/intel/cve-bin-tool/pull/4206)

Designing a database requires careful consideration. We need to think about scalability, speed, and the ability to adapt to changes. This week, I spent more time discussing these design decisions with my
mentor. We delved into various pros and cons. Finally, we came up with the following schema along with an index that will help make queries to the database faster.
```sql

CREATE TABLE IF NOT EXISTS deduplication (
    purl TEXT,
    vendor TEXT,
    PRIMARY KEY (purl, vendor)
);

CREATE INDEX IF NOT EXISTS purl_index ON deduplication (purl);
```

This schema is not yet finalized. We are still debating whether to include a field for product information. I believe it will become more refined over time.

While implementing this, I discovered that we had a test which was unnecessary and didn't cater to our needs. Therefore, I removed it and made some minor changes to the codebase.

## What's coming up next week?

For the upcoming week, I plan to:

- Figure out a way to populate de-duplication database using Pull Requests.
- Figure out directory/file structure for those Pull Requests.

To populate the database, we have decided to use PRs. When a name collision is found, the user will create a PR with information about the collision. In the upcoming week, I will work on figuring out an
optimal process and the file/directory structure for these PRs.

## Did you get stuck anywhere?

As a beginner in database design, it was challenging to decide which approach was most suitable for our case. However, with help from my mentor, it wasn't too difficult.


That's all for today! Tune in next week ;)
