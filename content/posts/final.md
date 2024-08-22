---
title: "GSoC: Final Report"
date: 2024-08-21
description: ""
type: "post"
---

![GSoC 2024](https://developers.google.com/open-source/gsoc/resources/downloads/GSoC-logo-horizontal-800.png)

# Google Summer of Code 2024 Final Report
- **Name**: Meet Soni ([@inosmeet](https://github.com/inosmeet))
- **Organization**: [Python Software Foundation](https://www.python.org/psf/)
- **Sub-organization**: [cve-bin-tool](https://github.com/intel/cve-bin-tool)
- **Project**: [Product Mapping using PURLs](https://summerofcode.withgoogle.com/programs/2024/projects/aEIXRpxg)
- **Proposal**: [View/Download](https://drive.google.com/file/d/1NzNoKssQiknqXw0TDaIgIFZWhnGcRJZ4/view)
----

## Summary


### Project Overview
Over the course of GSoC 2024, my project aimed to enhance the `cve-bin-tool` by improving its product mapping capabilities to reduce false positives. Initially, the tool relied on explicit, pre-defined
mappings between binary signatures and a list of CPE identifiers. However, this approach had significant limitations. As vulnerabilities evolved and new components emerged, maintaining these mappings 
required frequent updates, and the tool struggled with arbitrary product names, such as those found in Rust's `Cargo.lock` files.

To address these issues, my project focused on implementing a more robust and flexible mapping system that integrates seamlessly with the tool's existing structure. This new system leverages the 
`purl2cpe` database to handle varied and previously unsupported product names more effectively. By utilizing the `purl2cpe` database, the system reduces the need for constant updates and improves the
accuracy of vulnerability detection.

### What is purl2cpe ?
The purl2cpe is a database that contains relations between CPEs (Common Product Enumerator) and PURLs (Package URL). PURL is an open specification that standardizes identification and location of software
packages/versions in their respective repositories.

While CPEs provide a precise identification for components and versions, they do not provide an easy way to connect these vulnerable component versions with their respective Open Source repositories. 
These connections must be made available by human curation.

purl2cpe makes it easy for anyone to monitor the packages they use for known vulnerabilities.

### Why We Needed the Mismatch Database
To further reduce false positives, especially in cases where `purl2cpe` does not find a match, we developed the mismatch database. Previously, when no match was found, the tool would revert to searching
product names directly, which led to incorrect associations with vulnerabilities. The mismatch database serves as a source of “anti-matching” information, ensuring that similarly named but unrelated 
products do not cause false positives.

### Potential Uses Beyond cve-bin-tool
While initially intended for `cve-bin-tool`, this database has the potential to be useful outside of the project as well. By making it available, we hope to support efforts in the broader community to
de-duplicate similarly named software components and enhance the accuracy of vulnerability management tools.

### Resolving Key Issues
Through this project, I was able to resolve key issues identified in the community ([issue #3152](https://github.com/intel/cve-bin-tool/issues/3152), [issue #3179](https://github.com/intel/cve-bin-tool/issues/3179)),
contributing to a more reliable and scalable solution for vulnerability management.

## Tasks Achieved

- Integrate purl2cpe database:

  PRs:
  - [intel/cve-bin-tool#4159](https://github.com/intel/cve-bin-tool/pull/4159)
  - [intel/cve-bin-tool#4164](https://github.com/intel/cve-bin-tool/pull/4164)
  - [intel/cve-bin-tool#4179](https://github.com/intel/cve-bin-tool/pull/4179)
  - [intel/cve-bin-tool#4188](https://github.com/intel/cve-bin-tool/pull/4188)
  - [intel/cve-bin-tool#4332](https://github.com/intel/cve-bin-tool/pull/4332)

- Mismatch database:

  PRs:
  - [intel/cve-bin-tool#4206](https://github.com/intel/cve-bin-tool/pull/4206)
  - [intel/cve-bin-tool#4223](https://github.com/intel/cve-bin-tool/pull/4223)
  - [intel/cve-bin-tool#4225](https://github.com/intel/cve-bin-tool/pull/4225)
  - [intel/cve-bin-tool#4236](https://github.com/intel/cve-bin-tool/pull/4236)
  - [intel/cve-bin-tool#4239](https://github.com/intel/cve-bin-tool/pull/4239)
  - [intel/cve-bin-tool#4245](https://github.com/intel/cve-bin-tool/pull/4245)
  - [intel/cve-bin-tool#4246](https://github.com/intel/cve-bin-tool/pull/4246)
  - [intel/cve-bin-tool#4247](https://github.com/intel/cve-bin-tool/pull/4247)
  - [intel/cve-bin-tool#4248](https://github.com/intel/cve-bin-tool/pull/4248)
  - [intel/cve-bin-tool#4264](https://github.com/intel/cve-bin-tool/pull/4264)
  - [intel/cve-bin-tool#4268](https://github.com/intel/cve-bin-tool/pull/4268)
  - [intel/cve-bin-tool#4269](https://github.com/intel/cve-bin-tool/pull/4269)
  - [intel/cve-bin-tool#4280](https://github.com/intel/cve-bin-tool/pull/4280)
  - [intel/cve-bin-tool#4283](https://github.com/intel/cve-bin-tool/pull/4283)
  - [intel/cve-bin-tool#4292](https://github.com/intel/cve-bin-tool/pull/4292)
  - [intel/cve-bin-tool#4356](https://github.com/intel/cve-bin-tool/pull/4356)

- Convert Mismatch database into a standalone entity:

  PRs:
  - [intel/cve-bin-tool#4300](https://github.com/intel/cve-bin-tool/pull/4300)
  - [intel/cve-bin-tool#4346](https://github.com/intel/cve-bin-tool/pull/4346)
  - [intel/cve-bin-tool#4348](https://github.com/intel/cve-bin-tool/pull/4348)

## Future Work

### Expanding the Mismatch Database
The current implementation of the mismatch database focuses primarily on vendors. This approach is useful but faces challenges when dealing with unknown vendors. As highlighted in 
[issue #3193](https://github.com/intel/cve-bin-tool/issues/3193), unknown vendors can lead to gaps in data and unresolved mismatches.

To address these limitations, there is potential to expand the database to include additional attributes such as invalid purls and more. By broadening the scope, we can enhance the database's ability to
handle complex cases, improve the accuracy of vulnerability detection, and reduce the likelihood of false positives.

## What stood out to me:

What I really enjoyed during this period was having the freedom to make decisions and try things my way. It felt great to have that level of ownership. Working alongside industry experts was a huge bonus—
I got to learn from their experience while still having the space to explore and grow on my own. Overall, it was a super empowering experience.

Looking back, If I had a chance to do it all over again, I’d just sprinkle in a bit more structure to balance the freedom with some checkpoints—because even the best adventures can benefit from a few 
guiding stars.

----
I want to extend my heartfelt thanks to **Google** for providing this incredible opportunity through the GSoC program. It’s been an amazing journey of learning and growth. A big thank you to the **Python 
Software Foundation** for fostering such a vibrant community.

I’m especially grateful to my mentors, **[Terri Oda](https://github.com/terriko)**, **[Anthony Harrison](https://github.com/anthonyharrison)** and **[Ben Lewis](https://github.com/ben-zen)**. Your guidance,
patience, and encouragement made all the difference. Thank you for believing in me and helping me navigate this project with confidence. This experience wouldn’t have been the same without your support.

Lastly, a shoutout to my fellow GSoC contributor, **[Sanskar](https://github.com/mastersans)**. Collaborating with you made this journey even more rewarding. I’m glad we could support each other along the
way.
