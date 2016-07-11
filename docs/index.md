# Welcome to Laracogs

Welcome to Laracogs a provider of cogs to build your next amazing application including: a starter kit, form-maker, CRUD builder, documentation builder, and cryptography tool.
Laracogs is a package which can be added to any Laravel 5.1+ app. It's best to integrate it early and utilize the starter kit to hit the ground running.

----

### Installation

Start a new Laravel project:

Then run the following to add Laracogs
```php
composer require "yab/laracogs"
```

Add this to the `config/app.php` in the providers array:
```php
Yab\Laracogs\LaracogsProvider::class
```

Time to publish those assets!
```php
php artisan vendor:publish --provider="Yab\Laracogs\LaracogsProvider"
```

You now have Laracogs installed. Looking to try the *Starter Kit* look below.

<div class="thumbnail">
    <a href="/docs/img/screen1.jpg"><img alt="" src="/docs/img/screen1.jpg" /></a>
</div>
<div class="row">
    <div class="col-md-6">
        <div class="thumbnail">
            <a href="/docs/img/screen2.jpg"><img alt="" src="/docs/img/screen2.jpg" /></a>
        </div>
    </div>
    <div class="col-md-6">
        <div class="thumbnail">
            <a href="/docs/img/screen3.jpg"><img alt="" src="/docs/img/screen3.jpg" /></a>
        </div>
    </div>
</div>
<div class="row">
    <div class="col-md-6">
        <div class="thumbnail">
            <a href="/docs/img/screen4.jpg"><img alt="" src="/docs/img/screen4.jpg" /></a>
        </div>
    </div>
    <div class="col-md-6">
        <div class="thumbnail">
            <a href="/docs/img/screen5.jpg"><img alt="" src="/docs/img/screen5.jpg" /></a>
        </div>
    </div>
</div>

### Starter
In order to make use of the <u>starter kit</u> you will need to modify some files. Check out the modifications below:

Add the following to your `app/Http/Kernel.php` $routeMiddleware array.

```php
'admin' => \App\Http\Middleware\Admin::class,
'permission' => \App\Http\Middleware\Permission::class,
'roles' => \App\Http\Middleware\Roles::class,
```

Update the `App\User::class` in: 'config/auth.php' and 'database/factory/ModelFactory.php' to this:

```php
App\Repositories\User\User::class
```

Add the following to 'app/Providers/AuthServiceProvider.php' in the boot method

```php
$gate->define('admin', function ($user) {
    return ($user->roles->first()->name === 'admin');
});

$gate->define('team-member', function ($user, $team) {
    return ($user->teams->find($team->id));
});
```

You will want to create an sqlite memory test database in the `config/database.php`

```php
'testing' => [
    'driver'   => 'sqlite',
    'database' => ':memory:',
    'prefix'   => '',
],
```

Add the following line to the 'phpunit.xml' file
```xml
<env name="DB_CONNECTION" value="testing"/>
<env name="MAIL_DRIVER" value="log"/>
```

##### For Laravel 5.2
You will also need to set the location of the email for password reminders. (config/auth.php - at the bottom)

```php
'passwords' => [
    'users' => [
        'provider' => 'users',
        'email' => 'emails.password',
        'table' => 'password_resets',
        'expire' => 60,
    ],
],
```

##### Things to note
You may try and start quickly by testing the registration but please make sure your app's <u>email</u> is configured or it will throw an exception.
You can do this in the `.env` file easily by setting it to 'log' temporarily

```php
MAIL_DRIVER=log
```

##### Last Steps

Once you've added in all these parts you will want to run the starter command!

```php
php artisan laracogs:starter
```

Then you'll need to migrate to add in the users, user meta, roles and teams tables. The seeding is run to set the initial roles for your application.

```php
php artisan migrate --seed
```

## Also Provides
The Laracogs package also provides the LaravelCollective HTML, and Forms components.

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-39444410-8', 'auto');
  ga('send', 'pageview');

</script>
