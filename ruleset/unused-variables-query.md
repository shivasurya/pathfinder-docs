---
title: Unused Variables Query
layout: default
parent: Pathfinder Queries
---

## Unused Variables Query  

{: .label .label-purple }
New Rule

Pathfinder supports querying for unused variables in the source code. The query is designed to identify variables that are declared but not used in the source code.

### Query Syntax

The query syntax is simple, easy to use and inspired by SQL. The `has_access` routine is used to check if the variable is being accessed based on the scope.

```bash
# Query to find unused variables in the source code
# ruleid: unused-variables-query
# language: java
# description: Unused variables detected in the source code
# category: productivity, maintainability, clean-code
# confidence: high
# priority: high
# tags: code-smell, unused-variable 
FIND variable_declaration WHERE has_access = false AND scope = 'local'
```


