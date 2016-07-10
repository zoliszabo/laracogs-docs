# CRUD

One of the most powerful tools in the Laracogs arsenal is the CRUD builder. Following SOLID principals it can construct a basic set of components pending on a table name provided in the CLI. The CRUD can be used with singular table entities think: 'books' or 'authors' but, you can also build CRUDs for combined entities that is a parent, and child like structure: 'books_authors'. This will generate a 'books_authors' table and place all components of the authors (controller, repository, model etc) into a Books namespace, which means you can then generate 'books_publishers' and have all the components be added as siblings to the authors. Now let's say you went ahead with using the Laracogs starter kit, then you can autobuild your CRUDs with them bootstrapped, which means they're already wrapped up as view extensions of the dashboard content which means you're even closer to being done your application.

```
php artisan laracogs:crud {name or snake_names} {--api} {--bootstrap} {--semantic} {--serviceOnly} {--migration} {--schema} {--relationships} {--withFacades}
```

### API

The API option will add in a controller to handle API requests and responses. It will also add in the API routes assuming this is v1.

### Bootstrap &amp; Semantic
These are the two primarily supported CSS frameworks, you can opt in for either or disregard them completely. Both expect a dashboard parent view, this can be generated with either of the following commands:

```
artisan laracogs:bootstrap
artisan laracogs:semantic
```

These reskin your views with either of the CSS frameworks.

### Service Only

The service only will allow you to generate CRUDs that are service layer and lower this includes: Service, Repository, Model, and Tests with the options for migrations. It will skip the Controllers, Routes, Views, etc. This keeps your code lean, and is optimal for relationships that don't maintain a 'visual' presence in your site/app such as downloads of an entity.

### Migration

The migration option will add the migration file to your migrations directory, using the schema builder will fill in the create table method.

### Schema (Requires migration option)
You can define the table schema with the structure below. The field types should match what would be the Schema builder.

```
--schema="id:increments,name:string"
```

The following column types are available:
 * bigIncrements
 * increments
 * bigInteger
 * binary
 * boolean
 * char
 * date
 * dateTime
 * decimal
 * double
 * enum
 * float
 * integer
 * ipAddress
 * json
 * jsonb
 * longText
 * macAddress
 * mediumInteger
 * mediumText
 * morphs
 * smallInteger
 * string
 * string
 * text
 * time
 * tinyInteger
 * timestamp
 * uuid

### Relationships (Requires migration option)

You can specifiy relationships, in order to automate a few more steps of building your CRUDs. You can set the relationship expressions like this:

`relation|class|name`

or something like:

`hasOne|App\Author|author`

This will add in the relationships to your models, as well as add the needed name_id field to your tables. Just one more thing you don't have to worry about.

### With Facades

If you opt in for Facades the CRUD will generate them, with the intention that they will be used to access the service. You will need to bind them to the app in your own providers, but you will at least have the Facade file generated.

## Templates
All generated components are based on templates. There are basic templates included in this package, however in most cases you will have to conform them to your project's needs. If you have published the assets during the installation process, the template files will be available in `resources/laragocs/crud`. 

Test templates are treated differently from the other templates. By default there are three test templates provided, two integration tests for the generated service and repository, and one acceptance test. However, the Tests folder has a 'one to one' mapping with the tests folder of your project. This means you can easily add tests for different test levels matching your project. For example, if you want to create a unit test for the generated controller, you can just create a new template file, for instance `resources/laracogs/crud/Tests/Unit/ControllerTest.txt`. When running the CRUD generator, the following file will then be created: `tests/unit/NameOfResourceControllerTest.php`.


## Examples
The following components are generated:

Files Generated
------
* Controller
* Api Controller (optional)
* Service
* Repository
* Request
* Model
* Facade (optional)
* Views (Bootstrap or Semantic or CSS framework-less)
* Tests
* Migration (optional)
Appends to the following Files:
* app/Http/routes.php
* database/factories/ModelFactory.php

Single Word Example (Book):
------
```
php artisan laracogs:crud Book --migration --schema="id:increments,title:string,author:string"
```

When using the default paths for the components, the following files will be generated:

* app/Http/Controllers/BookController.php
* app/Http/Requests/BookRequest.php
* app/Repositories/Book/BookRepository.php
* app/Repositories/Book/Book.php
* app/Services/BookService.php
* resources/views/book/create.blade.php
* resources/views/book/edit.blade.php
* resources/views/book/index.blade.php
* resources/views/book/show.blade.php
* database/migrations/create_books_table.php
* tests/BookIntegrationTest.php
* tests/BookRepositoryTest.php
* tests/BookServiceTest.php

Snake Name Example (Book_Author):
------
```
php artisan laracogs:crud Book_Author --migration --schema="id:increments,firstname:string,lastname:string" --withFacades
```

When using the default paths for the components, the following files will be generated:

* app/Facades/Books/AuthorServiceFacade.php
* app/Http/Controllers/Books/AuthorController.php
* app/Http/Requests/Books/AuthorRequest.php
* app/Repositories/Books/Author/AuthorRepository.php
* app/Repositories/Books/Author/Author.php
* app/Services/Books/AuthorService.php
* resources/views/book/author/create.blade.php
* resources/views/book/author/edit.blade.php
* resources/views/book/author/index.blade.php
* resources/views/book/author/show.blade.php
* database/migrations/create_book_authors_table.php
* tests/Books/AuthorIntegrationTest.php
* tests/Books/AuthorRepositoryTest.php
* tests/Books/AuthorServiceTest.php

Single Name Example (Book with API):
------
```
php artisan laracogs:crud Book --api --migration --schema="id:increments,title:string,author:string"
```

When using the default paths for the components, the following files will be generated:

* app/Http/Controllers/Api/BookController.php
* app/Http/Controllers/BookController.php
* app/Http/Requests/BookRequest.php
* app/Repositories/Book/BookRepository.php
* app/Repositories/Book/Book.php
* app/Services/BookService.php
* resources/views/book/create.blade.php
* resources/views/book/edit.blade.php
* resources/views/book/index.blade.php
* resources/views/book/show.blade.php
* database/migrations/create_books_table.php
* tests/BookIntegrationTest.php
* tests/BookRepositoryTest.php
* tests/BookServiceTest.php

This is an example of what would be generated with the CRUD builder. It has all basic CRUD methods set.

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-39444410-8', 'auto');
  ga('send', 'pageview');
</script>
