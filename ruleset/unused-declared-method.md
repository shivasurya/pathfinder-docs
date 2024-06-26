---
title: Unused Method Query
layout: default
parent: Pathfinder Queries
---

## Unused Declared Method Query

{: .label .label-purple }
New Rule

Pathfinder supports querying for unused declared methods in the source code. The query is designed to identify methods that are declared but not used in the source code or invoked within the project.

### Query Syntax

The query syntax is simple, easy to use and inspired by SQL. The `has_access` routine is used to check if the method is being accessed across the project.

```bash
# Query to find unused declared methods in the source code
# ruleid: unused-declared-method-query
# language: java
# description: Unused declared methods detected in the source code
# category: productivity, maintainability, clean-code
# confidence: medium
# priority: high
# tags: code-smell, unused-method 
# false-positives: false positives are possible if there are implemented methods
FIND method_declaration WHERE has_access = false
```


