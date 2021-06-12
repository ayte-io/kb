---
title: Repository Maintenance Recommendations
layout: index
---

### Skeleton

Every repository, be it public or private, should have

- README.md
- [CHANGELOG.md](https://keepachangelog.com)
- .gitignore/.hgignore
- Sufficient documentation

Public repositories should also have LICENSE file or files. It is 
recommended to dual-license our own repositories with MIT and UPL-1.0 
licenses:

```
LICENSE-MIT
LICENSE-UPL-1.0
```

Commercial open-sourced products should be licensed with GPL.

### Flow

The exact flow, be it git flow, github flow or other, should adhere
to following rule set:

- Every release is maintained in `release/%major%.%minor%` branch.
- Master branch and dev branch are absent, development is advancing in 
corresponding release branches. Current release branch is set as main in
repo UI.
_ Everything else is like standard git-flow.
- Every feature takes single branch.
- Before merge, feature branches should be squashed at reasonable
level, ideally if every commit represents some complete change.
