mat-slideshow
=============

Polymer material slideshow using [materialize](http://materializecss.com/media.html) media slideshow component under the hood.

`bower install polymer-mat-slideshow`

### Troubleshoot

For some reason, currently having trouble with `this.each` in `materialize.js` not working as expected:

See: http://stackoverflow.com/questions/3106414/in-jquery-how-does-the-this-each-work

```js
return this.each(function() {
  // For each slider, we want to keep track of
  // which slide is active and its associated content
```

No idea why, not a jQuery plugin expert!

This element can be used something like this:

### Global Configuration

In `app/index.html`

```html
<head>
  <link rel="import" href="bower_components/polymer/polymer.html">  
  <link href="http://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
  <!-- Import materialize.css -->
  <link type="text/css" rel="stylesheet" href="../bower_components/materialize/dist/css/materialize.min.css"  media="screen,projection"/>
  <!-- jQuery 2 dependency -->
  <script type="text/javascript" src="https://code.jquery.com/jquery-2.1.1.min.js"></script>
  <!-- Import materialize.js -->
  <script type="text/javascript" src="../bower_components/materialize/dist/js/materialize.min.js"></script>
</head>
<body>
  <!-- use custom slideshow element -->
  <my-slideshow id="my-slideshow" slideshow="{{ slideshow }}"></my-slideshow>
```

### Import elements

In `app/elements/elements.html`

```html
<!-- element imports -->
<link rel="import" href="../bower_components/mat-slideshow/mat-slideshow.html">
<!-- app element imports -->
<link rel="import" href="elements/my-slideshow/my-slideshow.html">
```

### Use slideshow in custom element

Create custom element referenced by `index.html`

`app/elements/my-slideshow/my-slideshow.html`

```html
<dom-module id="my-slideshow">
  <style>
    :host {
      display: block;
    }
  </style>

  <template>
    <mat-slides options="{{ slideshow.options }}">
      <template is="dom-repeat" items="{{ slideshow.items }}" as="slide">
        <mat-slide image="{{ slide.image }}" caption="{{ slide.caption }}"></mat-slide>
      </template>
    </mat-slides>
  </template>

</dom-module>

<script>
  Polymer({
    is: 'my-slideshow',

    properties: {
      slideshow: Object
    }
  });
</script>
```

Dependencies
------------

Element dependencies are managed via [Bower](http://bower.io/). You can install that via:

```
npm install -g bower
```

Then, go ahead and download the element's dependencies:

```
bower install
```

Playing With Your Element
-------------------------

If you wish to work on your element in isolation, we recommend that you use[Polyserve](https://github.com/PolymerLabs/polyserve) to keep your element's bower dependencies in line. You can install it via:

```
npm install -g polyserve
```

And you can run it via:

```
polyserve
```

Once running, you can preview your element at`http://localhost:8080/components/mat-slideshow/`, where `mat-slideshow` is the name of the directory containing it.

Testing Your Element
--------------------

Simply navigate to the `/test` directory of your element to run its tests. If you are using Polyserve: `http://localhost:8080/components/mat-slideshow/test/`

### web-component-tester

The tests are compatible with [web-component-tester](https://github.com/Polymer/web-component-tester). Install it via:

```
npm install -g web-component-tester
```

Then, you can run your tests on *all* of your local browsers via:

```
wct
```

#### WCT Tips

`wct -l chrome` will only run tests in chrome.

`wct -p` will keep the browsers alive after test runs (refresh to re-run).

`wct test/some-file.html` will test only the files you specify.
