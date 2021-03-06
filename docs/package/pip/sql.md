# SQL Package Installation Plugin

Execute SQL instructions using a MySQL-flavored syntax.

!!! warning "This file is parsed by WoltLab Suite Core to allow reverting of certain changes, but not every syntax MySQL supports is recognized by the parser. To avoid any troubles, you should always use statements relying on the SQL standard."


## Expected Value

The `sql` package installation plugin expects a relative path to a `.sql` file.


## Features

### Logging

WoltLab Suite Core uses a SQL parser to extract queries and log certain actions.
This allows WoltLab Suite Core to revert some of the changes you apply upon package uninstallation.

The logged changes are:

- `CREATE TABLE`
- `ALTER TABLE … ADD COLUMN`
- `ALTER TABLE … ADD … KEY`

### Instance Number

It is possible to use different instance numbers, e.g. two separate WoltLab Suite Core installations within one database.
WoltLab Suite Core requires you to always use `wcf1_<tableName>` or `<app>1_<tableName>` (e.g. `blog1_blog` in WoltLab Suite Blog), the number (`1`) will be automatically replaced prior to execution.
If you every use anything other but `1`, you will eventually break things, thus always use `1`!

### Table Type

WoltLab Suite Core will determine the type of database tables on its own:
If the table contains a `FULLTEXT` index, it uses `MyISAM`, otherwise `InnoDB` is used.


## Limitations

### Logging

WoltLab Suite Core cannot revert changes to the database structure which would cause to the data to be either changed or new data to be incompatible with the original format.
Additionally, WoltLab Suite Core does not track regular SQL queries such as `DELETE` or `UPDATE`.

### Triggers

WoltLab Suite Core does not support trigger since MySQL does not support execution of triggers if the event was fired by a cascading foreign key action.
If you really need triggers, you should consider adding them by custom SQL queries using a [script](script.md).


## Example

`package.xml`:

```xml
<instruction type="sql">install.sql</instruction>
```

Example content:

{jinja{ codebox(
  title="install.sql",
  language="sql",
  filepath="package/pip/install.sql"
) }}