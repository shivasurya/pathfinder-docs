---
title: Basic Usage
layout: home
nav_order: 2
---

## Basic Query

Pathfinder supports basic queries search and filter entities in the source code. The query language is inspired by SQL and is designed to be simple and easy to use.
Entities supported so far are,

### Supported Entities

- `method_declaraion` : Represents a method declaration.
- `class_declaration` : Represents a class declaration.
- `method_invocation` : Represents a method invocation.
- `variable_declaration` : Represents a variable declaration.

### Supported Attributes

- `name` : Represents the name of the entity.
- `returntype` : Represents the return type of the entity.
- `visibility` : Represents the visibility of the entity (Access Modifiers).
- `argumentype` : Represents the argument types of the entity.
- `argumentname` : Represents the argument names of the entity.
- `superclass` : Represents the superclass of the entity. (Applicable only for class_declaration)
- `interface` : Represents the interfaces implemented by the entity. (Applicable only for class_declaration)
- `variabledatatype` : Represents the data type of the variable. (Applicable only for variable_declaration)
- `variablevalue` : Represents the value of the variable. (Applicable only for variable_declaration)
- `scope` : Represents the scope of the variable (example: local, field). (Applicable only for variable_declaration)

### Supported Routines

- `has_access` : Represents the routine to check if the entity is being accessed based on scope.

## Query Syntax

The query syntax is simple and easy to use. The syntax is inspired by SQL and is designed to be simple and easy to use.
Query does support complex conditions using `AND` and `OR` keywords and brackets.

### Syntax

Query declaration starts with the `FIND` keyword followed by the entity to search for. The query is followed by the `WHERE` keyword and the attribute to filter the results.

```sql
FIND method_declaration WHERE name = 'onCreate'
```

### Supported Operators

- `=` : Represents the equality operator.
- `!=` : Represents the not equal operator.

### Supported Keywords

- `FIND` : Represents the keyword to start the query.
- `WHERE` : Represents the keyword to filter the results.
- `AND` : Represents the keyword to combine multiple filters.
- `OR` : Represents the keyword to combine multiple filters.

### Examples

```sql
<!-- Find method declarations with name 'onCreate' and modifier as 'protected' -->
FIND method_declaration WHERE name = 'onCreate' AND visibility = 'protected'

<!-- Find method declarations with name 'onCreate' or modifier as 'protected' -->
FIND method_declaration WHERE name = 'onCreate' OR visibility = 'protected'

<!-- Find method declarations with name 'onCreate' and return type as 'void' -->
FIND method_declaration WHERE name = 'onCreate' AND returntype = 'void'

<!-- Find method declarations with name 'onCreate' and argument type as 'SQLiteDatabase' -->
FIND method_declaration WHERE name = 'onCreate' AND argumenttype = 'SQLiteDatabase'

<!-- Find method declarations with name 'onCreate' and argument name as 'db' -->
FIND method_declaration WHERE name = 'onCreate' AND argumentname = 'db'

<!-- Find method declarations with name 'onCreate' and argument name as 'db' and argument type as 'SQLiteDatabase' -->
FIND method_declaration WHERE name = 'onCreate' AND argumentname = 'db' AND argumenttype = 'SQLiteDatabase'
```

### Complex Queries

You can combine multiple filters using the `AND` and `OR` keywords to create complex queries with brackets.

```sql
<!-- Find method declarations with name 'onCreate' and modifier as 'protected' and return type as 'void' -->
FIND method_declaration WHERE name = 'onCreate' AND visibility = 'protected' AND returntype = 'void'

<!-- Find method declarations with name 'onCreate' and modifier as 'protected' or 'public' and return type as 'void' -->
FIND method_declaration WHERE name = 'onCreate' AND (visibility = 'protected' OR visibility = 'public') AND returntype = 'void'
```