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

## Kits!

* [The Starter Kit](Kits/starter.md)
* [API with JWT](Kits/api.md)
* [Billing with Cashier](Kits/billing.md)
* [Bootstrap Skins](Kits/bootstrap.md)
* [Semantic UI Skins](Kits/semantic.md)
* [Notifications](Kits/notifications.md)
* [Social Media Logins with Socialite](Kits/socialite.md)
* [Docs Generator](Kits/docs.md)

## Services!

We have a handful of services available to help you get your app written faster! Check them out:

* [CrudMaker](Services/crud.md)
* [CrudMaker: For exitsing table](Services/table-crud.md)
* [FormMaker](Services/form_maker.md)
* [InputMaker](Services/input_maker.md)
* [Crypto](Services/crypto.md)
