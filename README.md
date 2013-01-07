# About the Project

[![Build Status](https://secure.travis-ci.org/meltingice/CamanJS.png)](http://travis-ci.org/meltingice/CamanJS)

The main focus of CamanJS is manipulating images using the HTML5 canvas and Javascript. It's a combination of a simple-to-use interface with advanced and efficient image/canvas editing techniques. It is also completely library independent and can be safely used next to jQuery, YUI, Scriptaculous, MooTools, etc.

CamanJS is very easy to extend with new filters and plugins, and it comes with a wide array of image editing functionality, which is only growing as the community makes more plugins. All features that are not a part of the core CamanJS library are in a [separate plugins repository](https://github.com/meltingice/CamanJS-Plugins).

For more information, I highly recommend taking a look at the [official website](http://camanjs.com) where there is more comprehensive documentation and interactive demos. You can also [read the wiki](https://github.com/meltingice/CamanJS/wiki) for some basic information about the project and how to use it.

CamanJS is written in [Coffeescript](http://coffeescript.org) as of version 3.0. **It works both in-browser and in NodeJS.**

## Usage

Include one of the versions in the `dist/` folder, then you can run:

```js
Caman("#image-id", function () {
  this.brightness(10);
  this.contrast(20);
  this.render(function () {
    alert("Done!");
  });
});
```

Caman also supports modifying images via the `data-caman` HTML attribute. Simply separate each instruction with a space. Images with the `data-caman` attribute will automatically be modified at page load.

```html
<img data-caman="saturation(-10) brightness(20) vignette('10%')" src="path/to/image.jpg">
```

### HiDPI Support

Version 4 introduces better support for HiDPI (Retina) displays. It allows you to specify a higher resolution replacement using HTML data attributes. Keep in mind, however, that higher resolution images take longer to render.

**HTML data attributes**

* `data-caman-hidpi`: URL to the high resolution replacement image
* `data-caman-hidpi-disabled`: HiDPI support is enabled by default, so add this attribute if you wish to force disable it

## Development

If you are a developer who is contributing directly to the project, there are some tools to help you out.

### Building

To install all dependencies required for development, run `npm install -d`.

Because all plugins are in a separate repository, make sure you run:

```
git submodule init && git submodule update
```

To build, simply run `cake build`. The resulting files will be placed in the dist/ folder. Plugins will be automatically discovered and added to caman.full.js after the core library. You can also auto-compile when a file changes by using `cake watch`.

If you add any files to the core library, you will need to add them to the `coffeeFiles` array in the Cakefile. The point of this is so that order is preserved when generating the file JS file. Plugins do not need to be added to the Cakefile.

You will probably want to generate documentation if you make any changes. In addition to the normal requirements, you will also need the Python library Pygments.

To generate the documentation, run `cake docs`.

## CDN JS Hosting

CamanJS is hosted on CDN JS if you're looking for a CDN hosting solution. It is the full and minified version of the library, which means all plugins are included. Simply load CamanJS directly from [this URL](http://cdnjs.cloudflare.com/ajax/libs/camanjs/3.3.0/caman.full.min.js) for usage on your site.

## NodeJS Compatibility

CamanJS is fully compatible with NodeJS. The easiest way to install it is:

```
npm install caman
```

**Saving from NodeJS**

To save your modified image in NodeJS, simply call the save() function **after** rendering is finished by passing a callback function to `render()`. Trying to save before rendering is finished will cause issues.

``` coffeescript
Caman "./path/to/file.jpg", ->
  @brightness 40
  @render -> @save "./output.jpg"
```

# Testing

The test suite is currently under heavy expansion, but a number of tests exist for NodeJS, which test a good part of the core library. Browser-based tests still need to be written, mostly for initialization and proxy URL testing.

To run the NodeJS tests, run `npm test`.

# Project Contributors

* [Ryan LeFevre](http://twitter.com/meltingice) - Project Creator, Maintainer, and Lead Developer
* [Rick Waldron](http://twitter.com/rwaldron) - Plugin Architect and Developer
* [Cezar Sá Espinola](http://twitter.com/cezarsa) - Developer
* [Jarques Pretorius](http://twitter.com/jarques) - Logo Designer

# Plugin Contributors

* [Hosselaer](https://github.com/Hosselaer)
* [Mario Klingemann](http://www.quasimondo.com)
