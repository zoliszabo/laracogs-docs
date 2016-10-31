# LaraTest

Writing tests is always a good thing to do, but it can often eat up time with pesky details. In order to speed up building tests, we've made Laratest.

Now in as little as one command you can have half the writing of your tests done.

```
php artisan laratest:unit {path to file}
php artisan laratest:route {route name}
```

Using either of these commands will generate a basic test outline, with tests set for each of the public methods in the class, or in the case of the route any
applicable route (including resources) will have a corresponding test in place. All you have to do is refine it just a little.

