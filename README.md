mat-slideshow
=============

An element providing a starting point for your own reusable Polymer elements.

`bower install mat-slideshow`

It can be used something like this:

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

Then in `app/index.html` or some other place:

```html
<link rel="import" href="../bower_components/polymer/polymer.html">  
<link rel="import" href="../bower_components/mat-slideshow/slides.html">
<link rel="import" href="elements/my-slideshow/my-slideshow.html">
// ...
<body>
  <my-slideshow slideshow="{{ slideshow }}"></my-slideshow>
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
