---
blurb: The blob (Binary Large OBject) type represents an arbitrary binary object stored
  in the database system.
layout: docu
redirect_from:
- /docs/1.2/sql/data_types/blob
title: Blob Type
---

| Name | Aliases | Description |
|:---|:---|:---|
| `BLOB` | `BYTEA`, `BINARY`, `VARBINARY` | Variable-length binary data |

The blob (**B**inary **L**arge **OB**ject) type represents an arbitrary binary object stored in the database system. The blob type can contain any type of binary data with no restrictions. What the actual bytes represent is opaque to the database system.

Create a `BLOB` value with a single byte (170):

```sql
SELECT '\xAA'::BLOB;
```

Create a `BLOB` value with three bytes (170, 171, 172):

```sql
SELECT '\xAA\xAB\xAC'::BLOB;
```

Create a `BLOB` value with two bytes (65, 66):

```sql
SELECT 'AB'::BLOB;
```

Blobs are typically used to store non-textual objects that the database does not provide explicit support for, such as images. While blobs can hold objects up to 4 GB in size, typically it is not recommended to store very large objects within the database system. In many situations it is better to store the large file on the file system, and store the path to the file in the database system in a `VARCHAR` field.

## Functions

See [Blob Functions]({% link docs/1.2/sql/functions/blob.md %}).
