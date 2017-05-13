# Laracogs Documentation

<div class="logo">
    <span class="icon"></span>
</div>

Welcome to Laracogs a provider of cogs to build your next amazing application including: a starter kit, form-maker, CRUD builder, documentation builder, and cryptography tool.
Laracogs is a package which can be added to any Laravel 5.1+ app. It's best to integrate it early and utilize the starter kit to hit the ground running.

<img class="thumbnail img-33" alt="" src="./img/screens/starter/1.jpg" />
<img class="thumbnail img-33" alt="" src="./img/screens/billing/1.jpg" />
<img class="thumbnail img-33" alt="" src="./img/screens/notification/1.jpg" />

----

## Installation

Start a new Laravel project:

Then run the following to add Laracogs
```php
composer require "yab/laracogs"
```

Add this to the `config/app.php` in the providers array:
```php
Yab\Laracogs\LaracogsProvider::class
```

Time to publish those assets! Laracogs uses CrudMaker and FormMaker which have publishable assets.
```php
php artisan vendor:publish
```
or
```php
php artisan vendor:publish --provider="Yab\CrudMaker\CrudMakerProvider"
php artisan vendor:publish --provider="Yab\FormMaker\FormMakerProvider"
```


You now have Laracogs installed. Try out the *Starter Kit* below.

----

## Kits!

* [The Starter Kit](kits/starter.md)
* [API with JWT](kits/api.md)
* [Billing with Cashier](kits/billing.md)
* [Bootstrap Skins](kits/bootstrap.md)
* [Semantic UI Skins](kits/semantic.md)
* [Notifications](kits/notifications.md)
* [Features](kits/features.md)
* [Activity](kits/activity.md)
* [Social Media Logins with Socialite](kits/socialite.md)
* [Docs Generator](kits/docs.md)

## Services!

We have a handful of services available to help you get your app written faster! Check them out:

* [CrudMaker](services/crud.md)
* [CrudMaker: For exitsing table](services/table-crud.md)
* [FormMaker](services/form_maker.md)
* [InputMaker](services/input_maker.md)
* [Crypto](services/crypto.md)
* [Cerebrum](services/cerebrum.md)
* [Laratest](services/laratest.md)

----

## Design Philosophy

All code in one way or another follows some sort of philosophy or structure. Laracogs, and in turn the CrudMaker follow a pattern which enables strict rules for where which code belongs where as well as easy ways of scaling.
Lets start by looking at Micro-services.

Micro-services are single use/ purpose usually RESTful endpoints. Their goal is to do one thing and one thing only. Lets say we have a master database, but we want to have a contacts component in our app. We can make a contacts micro-service which has endpoints for managing them, then all logic pertaining to contacts will reside in the contacts microservice. How does this pertain to Laracogs and the CrudMaker?

#### Simple.

Laracogs can add basic boilerplate components to your app so you can start developing quickly. You may add on a contacts CRUD for example. The code pattern that we use makes it simple to for you as a dev to remove the Contacts component and make it a micro-service, or leave it inside your app.

#### Really?! How does that work?

Well, first off we follow a pattern of View <- Controller -> Service -> Model. Now in this pattern, Controller can be replaced with Console, or Controller/ Console and View can be completely removed. This means that a Controller's sole purpose is to call a Service, and pass the result to a View. The Service in turn contains all the logic and integration of third party services or other internal services, a service can talk to anything, models services etc. This makes it that a model is reduced to predominantly defining itself, and any relationships it has. This structure allows us to keep all layers of an application as lean as possible. It also enables us to remove a group (Controller/ Service/ Model) and make it a microservice while only having to modify one Service file in the original app.

By default the CrudMaker will assume you have no base Service. But, you could easily modify your templates to support a base class for each of these which would reduce the duplication in your code.

#### Scaleable and Simple

The purpose of all of this is to enable developers to handle scaling while maintaining simple code bases in any app they develop. Sometimes the only way to do that is with strict rules.

#### We're not perfect

If you think we're nuts please provide a reason, but we're always happy to discuss design pattern ideas and implementations.