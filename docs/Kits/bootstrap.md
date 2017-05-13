# Bootstrap UI

If you feel like opting in for the Laracogs starter kit. You also have a great bootstraping option for the views. You can blast through the initial building of an app and hit the groud running!

```
php artisan laracogs:bootstrap
```

!!! Tip "This will also ensure that your webpack file is prepared to run"

## What Boostrap Publishes

The command will overwrite any existing files with the bootstrap version of them:

* resources/views/
    * user/
        * meta.blade.php
        * password.blade.php
        * settings.blade.php
    * admin/
        * users/
            * edit.blade.php
            * index.blade.php
            * invite.blade.php
    * auth/
        * login.blade.php
        * password.blade.php
        * register.blade.php
        * reset.blade.php
    * dashboard/
        * main.blade.php
        * panel.blade.php
    * emails/
        * new-user.blade.php
        * password.blade.php
    * errors/
        * 404.blade.php
        * 503.blade.php
    * partials/
        * errors.blade.php
        * message.blade.php
    * team/
        * create.blade.php
        * edit.blade.php
        * index.blade.php
        * show.blade.php
