<!-- TITLE: Altertable -->
<!-- SUBTITLE: A quick summary of Altertable -->

# Alter enum column


```text
ALTER TABLE
    `table_name`
MODIFY COLUMN
    `column_name2` enum(
        'existing_value1',
        'existing_value2',
        'new_value1',
        'new_value2'
    )
```

# Add an Index to table


```text
ALTER TABLE mytable ADD INDEX name_idx (mycolumname);
```

