# Social Media Logins

If you feel like opting in for the Laracogs starter kit. You also have the option to utilize the socialite command. If you're looking to offer social media logins on your application and want a simple way to get started then look no further. Simply run the command and follow the steps below and you'll have GitHub login out of the box. Integrating Facebook etc afterward is easy when you look at the code base.

##### Requires
```php
composer require laravel/socialite
```

## Setup
```
php artisan laracogs:socialite
```

The next step is to prepare your app with socialite:

Add this to your app config under providers:
```php
Laravel\Socialite\SocialiteServiceProvider::class
```

Add this to your app config under aliases:
```php
'Socialite' => Laravel\Socialite\Facades\Socialite::class,
```

Add this to the `app/Providers/RouteServiceProvider.php` in the `mapWebRoutes(Router $router)` function:
```php
require app_path('Http/socialite-routes.php');
```

Finally set the access details in the services config:
```php
'github' => [
    'client_id' => 'id code',
    'client_secret' => 'secret code',
    'redirect' => 'http://your-domain/auth/github/callback',
    'scopes' => ['user:email'],
],
```

## What Socialite publishes
The command will overwrite any existing files with the socialite version of them:

* app/Http/Controllers/Auth/SocialiteAuthController.php
* app/Http/socialite-routes.php

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-39444410-8', 'auto');
  ga('send', 'pageview');

</script>
