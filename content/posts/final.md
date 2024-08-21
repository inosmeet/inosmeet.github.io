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

Over the course of GSoC 2024, my project aimed to enhance the `cve-bin-tool` by improving its product mapping capabilities to reduce false positives. Initially, the tool relied on explicit, pre-defined
mappings between binary signatures and a list of CPE identifiers. While effective, this approach required frequent updates as vulnerabilities evolved and was less effective when handling arbitrary product
names from component lists like Rust's `Cargo.lock` files. My project focused on addressing this limitation by implementing a more robust and flexible mapping system compatible with the existing structure 
of the tool. This new system reduces the need for constant updates and improves the accuracy of vulnerability detection, particularly in handling varied and previously unsupported product names. The 
changes introduced integrate seamlessly with the current implementation, requiring minimal adjustments and preserving the integrity of the tool's overall architecture.

Through this project, I was able to resolve key issues identified in the community ([#3152](https://github.com/intel/cve-bin-tool/issues/3152), [#3179](https://github.com/intel/cve-bin-tool/issues/3179)),
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

## What stood out to me:

What I really enjoyed during this period was having the freedom to make decisions and try things my way. It felt great to have that level of ownership. Working alongside industry experts was a huge bonus—
I got to learn from their experience while still having the space to explore and grow on my own. Overall, it was a super empowering experience.

----
I want to extend my heartfelt thanks to **Google** for providing this incredible opportunity through the GSoC program. It’s been an amazing journey of learning and growth. A big thank you to the **Python 
Software Foundation** for fostering such a vibrant community.

I’m especially grateful to my mentors, **[Terri Oda](https://github.com/terriko)**, **[Anthony Harrison](https://github.com/anthonyharrison)** and **[Ben Lewis](https://github.com/ben-zen)**. Your guidance,
patience, and encouragement made all the difference. Thank you for believing in me and helping me navigate this project with confidence. This experience wouldn’t have been the same without your support.

Lastly, a shoutout to my fellow GSoC contributor, **[Sanskar](https://github.com/mastersans)**. Collaborating with you made this journey even more rewarding. I’m glad we could support each other along the
way.
