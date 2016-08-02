# Application Notifications

If you feel like opting in for the Laracogs starter kit. You can also get your app's notifications handled quickly with Laracogs notifications command. Laracog's notifications will build a basic controller, views etc so you can easily notifiy your users, in bulk or specifically.

## Setup

```php
php artisan laracogs:notifications
```

You may want to add this line to your navigation:

```html
<li><a href="{!! url('user/notifications') !!}"><span class="fa fa-envelope-o"></span> Notifications</a></li>
<li><a href="{!! url('admin/notifications') !!}"><span class="fa fa-envelope-o"></span> Notifications</a></li>
```

Add this to the `app/Providers/RouteServiceProvider.php` in the `mapWebRoutes(Router $router)` function:

```php
require app_path('Http/notification-routes.php');
```

## Facades
Provides the following tool for in app notifications:

```php
Notifications::notify($userId, $flag, $title, $details);
```

<small>Flags can be any bootstrap alert: default, info, success, warning, danger</small>

## What Notifications Publishes:

The command will overwrite any existing files with the notification version of them:

* app/Facades/Notifications.php
* app/Http/Controllers/Admin/NotificationController.php
* app/Http/Controllers/User/NotificationController.php
* app/Http/notification-routes.php
* app/Http/Requests/NotificationRequest.php
* app/Repositories/Notification/Notification.php
* app/Repositories/Notification/NotificationRepository.php
* app/Services/NotificationService.php
* database/migrations/2016_04_14_180036_create_notifications_table.php
* resources/views/admin/notifications/create.blade.php
* resources/views/admin/notifications/edit.blade.php
* resources/views/admin/notifications/index.blade.php
* resources/views/notifications/index.blade.php
* resources/views/notifications/show.blade.php
* tests/NotificationIntegrationTest.php
* tests/NotificationRepositoryTest.php
* tests/NotificationServiceTest.php
