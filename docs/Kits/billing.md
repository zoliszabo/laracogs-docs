# Application Billing

If you feel like opting in for the Laracogs starter kit. You can also get your app's billing handled quickly with Laracogs billing command and `Laravel/Cashier`. Laracog's billing will build a basic controller, views etc so you can stay focused on what makes your application amazing!

##### Requires
```php
composer require laravel/cashier
```

## Setup
```
php artisan laracogs:billing
```

Add this to the `app/Providers/RouteServiceProvider.php` in the `mapWebRoutes(Router $router)` function:
```php
require app_path('Http/billing-routes.php');
```

Add this to the .env:
```php
SUBSCRIPTION=basic
STRIPE_SECRET=secret-key
STRIPE_PUBLIC=public-key
```

Add this to the app/Providers/AuthServiceProvider.php:
```php
$gate->define('access-billing', function ($user) {
    return ($user->meta->subscribed('main') && is_null($user->meta->subscription('main')->endDate));
});
```

And for the `config/services.php` you will want yours to resemble:
```php
'stripe' => [
    'model'  => App\Repositories\UserMeta\UserMeta::class,
    'key'    => env('STRIPE_PUBLIC'),
    'secret' => env('STRIPE_SECRET'),
],
```

Finally run migrate to add the subscriptions and bind them to the user meta:
```php
php artisan migrate
```

You will also want to update your gulpfile.js to include the card.js, and subscription.js
```js
elixir(function(mix) {
    mix.scripts([
        'app.js',
        'card.js',
        'subscription.js'
    ]);
});
```

### After Setup
You may want to add this line to your navigation:

```php
<li><a href="{!! url('user/billing/details') !!}"><span class="fa fa-dollar"></span> Billing</a></li>
```

### Notes
You may want to switch the line in the view vendor.receipt to:

```php
<strong>To:</strong> {{ $user->user()->email }}
```

We do this because rather than bind the billing to the User, we bound it to the UserMeta.

## What Billing Publishes

The command will overwrite any existing files with the billing version of them:

* app/Http/Controllers/User/BillingController.php
* app/Http/billing-routes.php
* app/Repositories/UserMeta/UserMeta.php
* config/invoice.php
* config/plans.php
* database/migrations/2016_02_26_000647_create_subscriptions_table.php
* database/migrations/2016_02_26_000658_add_billings_to_user_meta.php
* resources/assets/js/card.js
* resources/assets/js/subscription.js
* resources/views/billing/card-form.blade.php
* resources/views/billing/change-card.blade.php
* resources/views/billing/details.blade.php
* resources/views/billing/invoices.blade.php
* resources/views/billing/coupons.blade.php
* resources/views/billing/subscribe.blade.php
* resources/views/billing/tabs.blade.php

## Accounts

The Account service is a tool for handling your subscription details, meaning you can limit your applications based on various clauses using the plans config. You're free to set these plan details restricting things within a billing cycle or just in general.

These are relative to *billing* only. They provide extra tools for handling restrictions in your application based on the plan the user subscribed to. Unless you implment the cashier billing system with the UserMeta structure provided by Laracogs it will not benefit you.

### Config
This is the basic config for `config/plans.php`.

```
'subscription_name' => 'main',
'plans' => [
    'basic' => [
        'access' => [
            'some name'
        ],
        'limits' => [
            'Model\Namespace' => 5,
            'pivot_table' => 1
        ],
        'credits' => [
            'column' => 'credits_spent',
            'limit' => 10
        ],
        'custom' => [
            'anything' => 'anything'
        ],
    ],
]
```

### Service Methods

##### currentBillingCycle()
By using this method at the beginning and chaining another method after it you enable the restriction of the query to be performed but restricting itself to the current billing cycle.

##### canAccess($area)
Retuns a boolean if the user can enter

##### cannotAccess($area)
Retuns a boolean if the user cannot enter

##### getClause($key)
Returns the specified clause of the plans

##### getLimit($model)
Returns the specified limit of a model or pivot table

##### withinLimit($model, $key = 'user_id', $value = {user's id})
Confirms that the specified model only has the specified amount collected by the $key and $value.
* If you add the `currentBillingCycle()` before this then it would add the further restrictions.

##### creditsUsed($model, $key = 'user_id', $value = {user's id})
Reports back the specified amount collected by the $key and $value.
* If you add the `currentBillingCycle()` before this then it would add the further restrictions.

##### creditsAvailable($model)
Returns the number of credits remaining based on the config and the previous method.
* If you add the `currentBillingCycle()` before this then it would add the further restrictions.

##### clause($key, $method, $model = null)
Performs a custom method with rules defined by the clause name in the config. The Closure method in this is provided with the following parameters: $user, $subscription, $clause, $query


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-39444410-8', 'auto');
  ga('send', 'pageview');

</script>
