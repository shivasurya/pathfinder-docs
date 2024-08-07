---
title: Home
layout: home
nav_order: 1
---

## Code Pathfinder

Introducing Code Pathfinder, the open-source alternative to CodeQL. Designed for precise flow analysis and advanced structural search, it identifies vulnerabilities in your code. Currently optimized for Java, Code Pathfinder offers robust query support to enhance your code's security and integrity.

[Get started now](#installation){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[View it on GitHub](https://github.com/shivasurya/code-pathfinder){: .btn .fs-5 .mb-4 .mb-md-0 }

### Features

- **Basic query support**: Write queries to search for patterns in source code.
- **Call graph analysis**: Analyze method calls and data flow between methods.
- **Source Sink analysis**: Identify sources and sinks of sensitive data and check for vulnerabilities like SQL injection, XSS etc.

### Installation

```bash
$ git clone https://github.com/shivasurya/code-pathfinder
$ cd sourcecode-parser
$ go build -o pathfinder (or) go run .
$ ./pathfinder /PATH/TO/SOURCE
```

### Usage

```bash
$ ./pathfinder /PATH/TO/SOURCE
2024/06/30 21:35:29 Graph built successfully
Path-Finder Query Console: 
>FIND method_declaration WHERE throwstype = "ClassCastException"
Executing query: FIND method_declaration WHERE throwstype = "ClassCastException"

┌───┬──────────────────────────────────────────┬─────────────┬────────────────────┬────────────────┬──────────────────────────────────────────────────────────────┐
│ # │ FILE                                     │ LINE NUMBER │ TYPE               │ NAME           │ CODE SNIPPET                                                 │
├───┼──────────────────────────────────────────┼─────────────┼────────────────────┼────────────────┼──────────────────────────────────────────────────────────────┤
│ 1 │ /Users/shiva/src/code-pathfinder/test-sr │         148 │ method_declaration │ getPaneChanges │ protected void getPaneChanges() throws ClassCastException {  │
│   │ c/android/app/src/main/java/com/ivb/udac │             │                    │                │         mTwoPane = findViewById(R.id.movie_detail_container) │
│   │ ity/movieListActivity.java               │             │                    │                │  != null;                                                    │
│   │                                          │             │                    │                │     }                                                        │
└───┴──────────────────────────────────────────┴─────────────┴────────────────────┴────────────────┴──────────────────────────────────────────────────────────────┘
Path-Finder Query Console: 
>:quit
Okay, Bye!
```


