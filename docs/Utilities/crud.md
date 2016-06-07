# CRUD

One of the most powerful tools in the Laracogs arsenal is the CRUD builder. Following SOLID principals it can construct a basic set of components pending on a table name provided in the CLI. The CRUD can be used with singular table entities think: 'books' or 'authors' but, you can also build CRUDS for combined entities that is a parent, and child like structure: 'books_authors'. This will generate a 'books_authors' table and place all components of the authors (controller, repository, model etc) into a Books namespace, which means you can then generate 'books_publishers' and have all the components be added as siblings to the authors. Now let's say you went ahead with using the Laracogs starter kit, then you can autobuild your CRUDs with them boostrapped, which means they're already wrapped up as view extensions of the dashboard content which means you're even closer to being done your application.

```
php artisan laracogs:crud {name or snake_names} {--api} {--migration} {--bootstrap} {--semantic} {--schema} {--serviceOnly}
```

## Service Only

The service only will allow you to generate CRUDs that are service layer and lower this includes: Service, Repository, Model, and Tests with the options for migrations. It will skip the Controllers, Routes, Views, etc. This keeps your code lean, and is optimal for relationships that don't maintain a 'visual' presence in your site/app such as downloads of an entity.

### Bootstrap &amp; Semantic
These are the two primarily supported CSS frameworks, you can opt in for either or disregard them completely. Both expect a dashboard parent view, this can be generated with either of the following commands:

```
artisan laracogs:bootstrap
artisan laracogs:semantic
```

These reskin your views with either of the CSS frameworks.

### Schema
You can define the table schema with the structure below. The field types should match what would be the Schema builder.

```
--schema="id:increments,name:string"
```

### Example:
The following components are generated:

Files Generated
------
* Controller
* Api Controller (optional)
* Service
* Repository
* Request
* Model
* Facade
* Views (Bootstrap or Semantic or CSS framework-less)
* Tests
* Migration (optional)
Appends to the following Files:
* app/Http/routes.php
* database/factories/ModelFactory.php

Example (Book):
------
* app/Facades/BookServiceFacade.php
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

Example (Book with API):
------
* app/Facades/BookServiceFacade.php
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
