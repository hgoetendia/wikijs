<!-- TITLE: Createtypes -->
<!-- SUBTITLE: A quick summary of Createtypes -->

# Enumerated type


```pgsql
CREATE TYPE bug_status AS ENUM ('new', 'open', 'closed');

CREATE TABLE bug (
    id serial,
    description text,
    status bug_status
);

```

# Composite type


```pgsql
CREATE TYPE compfoo AS (f1 int, f2 text);

CREATE FUNCTION getfoo() RETURNS SETOF compfoo AS $$
    SELECT fooid, fooname FROM foo
$$ LANGUAGE SQL;
```
