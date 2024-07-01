---
title: Avoid Deprecated Callable Access
layout: default
parent: Pathfinder Queries
---

## Avoid Deprecated Callable Access Query

{: .label .label-purple }
New Rule

Pathfinder supports querying for deprecated callable access in the source code. The query is designed to identify deprecated callable access in the source code.

### Query Syntax

The query syntax is simple, easy to use and inspired by SQL. The `has_access` routine is used to check if the callable is being accessed across the project.

```bash
# Query to find deprecated callable access in the source code
# ruleid: avoid-deprecated-callable-access
# language: java
# description: Using a method that has been marked as deprecated may be dangerous or fail to take advantage of a better method
# category: maintainability, non-attributable
# security-rule: CWE-477
# priority: high
# confidence: high
# tags: deprecated, code-smell

FIND method_declaration WHERE annotation = "@Deprecated" AND has_access = "true"
```


