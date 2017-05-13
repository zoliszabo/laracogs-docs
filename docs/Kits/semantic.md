# Semantic UI

If you feel like opting in for the Laracogs starter kit. You also have a great option for the views with Semantic UI. You can blast through the initial building of an app and hit the groud running! Utilizing the Semantic UI components.

```
php artisan laracogs:semantic
```

After installation is complete you will need to install semantic-ui:

```
'npm install semantic-ui'
```

When prompted, select `automatic detection`.
When prompted, select your `project location`, default should be fine.
When prompted, set the directory to: `semantic`

Then run:

```
'cd semantic && gulp build'
```

Then run:

```
'cd ../ && npm run dev'
```

Make sure you set the `PagesController@dashboard` to use the following view:

```
'dashboard.main'
```

Finished setting up semantic-ui in your app


The command will overwrite any existing files with the semantic version of them:

## What Semantic Publishes

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
