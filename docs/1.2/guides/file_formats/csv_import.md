---
layout: docu
redirect_from:
- /docs/1.2/guides/import/csv_import
- /docs/1.2/guides/import/csv_import/
- /docs/1.2/guides/file_formats/csv_import
title: CSV Import
---

To read data from a CSV file, use the `read_csv` function in the `FROM` clause of a query:

```sql
SELECT * FROM read_csv('input.csv');
```

Alternatively, you can omit the `read_csv` function and let DuckDB infer it from the extension:

```sql
SELECT * FROM 'input.csv';
```

To create a new table using the result from a query, use [`CREATE TABLE ... AS SELECT` statement]({% link docs/1.2/sql/statements/create_table.md %}#create-table--as-select-ctas):

```sql
CREATE TABLE new_tbl AS
    SELECT * FROM read_csv('input.csv');
```

We can use DuckDB's [optional `FROM`-first syntax]({% link docs/1.2/sql/query_syntax/from.md %}) to omit `SELECT *`:

```sql
CREATE TABLE new_tbl AS
    FROM read_csv('input.csv');
```

To load data into an existing table from a query, use `INSERT INTO` from a `SELECT` statement:

```sql
INSERT INTO tbl
    SELECT * FROM read_csv('input.csv');
```

Alternatively, the `COPY` statement can also be used to load data from a CSV file into an existing table:

```sql
COPY tbl FROM 'input.csv';
```

To load data into an existing table where the table has more columns than the CSV file, you can use the [`INSERT INTO ... BY NAME` clause]({% link docs/1.2/sql/statements/insert.md %}#insert-into--by-name):

```sql
INSERT INTO tbl BY NAME
    SELECT * FROM read_csv('input.csv');
```

For additional options, see the [CSV import reference]({% link docs/1.2/data/csv/overview.md %}) and the [`COPY` statement documentation]({% link docs/1.2/sql/statements/copy.md %}).
