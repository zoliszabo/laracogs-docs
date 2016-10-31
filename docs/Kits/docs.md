# Docs

The docs generator is a very easy to use tool to generate a micro-site of your business rules documentation. You can create basic markdown templates with one command and build the micro-site with another. You can also very easily generate a config for `Sami` to create documentation for your application's core structure.

## Create Template
```
php artisan laracogs:docs create {name}
```
A markdown file will be made in: `documentation/rules/`. The rule builder will only go one layer deep in terms of a folder structure.

## Build Business Rules Site
```
php artisan laracogs:docs build
```
The microsite will be generated in the following directory: `documentation/build/rules/`. It will utilize the markdown files found in: `documentation/rules/`

## Create Sami Config
```
php artisan laracogs:docs sami
```
Laracogs will create a `SAMI` config and provide the commands required to run the build of the API docs. You will then find the new API documentation site: `documentation/build/api`
