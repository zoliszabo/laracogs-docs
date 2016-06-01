# Input Maker

The nice part about the input maker is that its the core of the form maker only pulled out. So this way you can reduce your HTML writing significanly with its blade directives or helpers.

## Blade Directives

```
@input_maker_label()
@input_maker_create()
```

## Helpers

```
input_maker_label()
input_maker_create()
```

## Facades

```
InputMaker::label()
InputMaker::create()
```

## Common Components

## Simple Fields For Everything!

The label generator is the easiest:

```
input_maker_label('name', ['class' => 'something'])
```

The input generator has a few more parts:

```
input_maker_create($name, $field, $object = null, $class = 'form-control', $reformatted = false, $populated = true)
```

The $field paramter is an array which can be highly configured.

### Example $feild Config

```
[
    'type' => '', // defaults to standard text input
    'placeholder' => 'User Name Goes Here!',
    'alt_name' => 'User Name',
    'custom' => 'custom DOM attributes etc',
    'class' => 'css class names',
    'before' => '<span class="input-group-addon" id="basic-addon1">@</span>',
    'after' => '<span class="input-group-addon" id="basic-addon2">@example.com</span>',
]
```

For Relationships:
```
[
    'model' => 'Full class as string',
    'label' => 'visible name for the options',
    'value' => 'value for the options',
]

Example without User:
@input_maker_create('roles', ['type' => 'relationship', 'model' => 'App\Repositories\Role\Role', 'label' => 'label', 'value' => 'name'])

Example with User:
@input_maker_create('roles', ['type' => 'relationship', 'model' => 'App\Repositories\Role\Role', 'label' => 'label', 'value' => 'name'], $user)
```

Types supported in the Config:

* string
* text (converts to textarea)
* password
* checkbox
* checkbox-inline
* radio
* select
* hidden
* number
* float
* decimal
* relationship

_** If no type is set the InputMaker will default to a standard text input_

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-39444410-8', 'auto');
  ga('send', 'pageview');

</script>
