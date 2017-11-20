---
title: Database
---
# Database

- [Tables and Fields](#tables)
- [Migrations](#migrations)
        
<a name="tables"></a>
## Tables and Fields
All table and fields to use snake_case.

Values should be stored in the lowest common denomination of that value that will be a integer and not a float or decimal, to allow for greatest accuracy.
- Currency should be stored as an integer of pence.
- Time should be stored as an integer of seconds instead of a decimal for minutes.
- Measurements in meters or centimeters should be stored as millimeters.

Columns should be structured in the following method

```
- ID
- Foreign Keys
- Fields
- Nullable Datetime fields
```

Fields should always be nullable, if the field can contain a NULL.

All foreign keys should contain an index, with the exception of a pivot table.

Be aware of mathematical calculations in code, if possible this should be saved in the database. This stops the calculation needing to be recalculated and gives a history if the calculation changes.

Be descriptive with column names (e.g. num_hours should be hours not minutes)

Foreign keys should be descriptive and using the table name where possible. But there are some scenarios where this will not work, especially when there are 2 user IDs (e.g. creator_id & updater_id).
```
user_id // table_name only isn't necessarily descriptive enough
creator_id // because it is the creator of the table
```

If there is business logic on the “type” of field, default to an enum. *e.g. Order status*

<a name="migrations"></a>
## Migrations
All database changes should be in migrations.

Do not use if statements in migrations, this is so that we see errors when a migration fails in case something has gone wrong.
e.g. don't check that table exists before creating, or that column exists. If they do and migration fails it should be corrected, not ignored.
