# Table CRUD

The table CRUD is a wrapper on the CRUD which will parse the table in the database and build the CRUD from that table.

*You must make sure the name matches the table name case wise*

```
php artisan crudmaker:table {name or snake_names}
{--api}
{--ui=bootstrap|semantic}
{--serviceOnly}
{--withFacade}
{--relationships}
```
