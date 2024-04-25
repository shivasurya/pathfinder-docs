---
title: Home
layout: home
---

## Code Pathfinder

Code Pathfinder attempts to be query language/flow analysis with structural search on source code. It's built for identifying vulnerabilities in source code. Currently, it only supports Java language.

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
2024/04/19 12:46:08 Graph built successfully
Path-Finder Query Console: 
> FIND method WHERE name = 'onCreate'
FIND method WHERE name = 'onCreate'
------Results------
@Override
public void onCreate(SQLiteDatabase db) {
    db.execSQL(DATABASE_CREATE);
}
-------
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_movie_detail);
    Intent intent = getIntent();

    getSupportActionBar().setDisplayHomeAsUpEnabled(true);
    getSupportActionBar().setDisplayShowHomeEnabled(true);

    movieGeneralModal moviegeneralModal = (movieGeneralModal) intent.getSerializableExtra("DATA_MOVIE");

    if (savedInstanceState == null) {

        movieDetailFragment fragment = new movieDetailFragment();
        fragment.setMovieData(moviegeneralModal);
        getSupportFragmentManager().beginTransaction()
                .add(R.id.movie_detail_container, fragment)
                .commit();
    }
}
------Results------
```


