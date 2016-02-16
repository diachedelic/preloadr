preloadr.js
================

Helper for images preloading, with :
 * optional callback after each load
 * optional callback at the end
 * possibility to force sequential loading of images

Usage
-----

``` html
<script src="preloadr.min.js"></script>
<!-- // defines preloadimages() -->
```

You can call it with an array or object of images.

 * The optional second parameter is the function that will be called after the loading of all images.
 * The optional third parameter is the function that will be called after each image is loaded.
 * The optional last parameter defines whether you want to force a sequential loading (each image is loaded after
the previous one has finished - note that 'finished' does not mean loaded, the image loading could have been aborted or unsuccesful -). Useful if you want to minimize bandwith consumtion. Default value : false.

```js
preloadr(['img1.png', 'img2.png'],
    function (images) {
        console.log("I've loaded " + images.length + " images !");
        // => "I've loaded 2 images"
    },
    function (images) {
        console.log("I've juste loaded : " + image.src);
        // => "I've just loaded img1.png"
        // => "I've just loaded img2.png"
    },
    false
);
```

or

```js
preloadr({ img1: 'img1.png', img2: 'img2.png' },
    function (image) {
        console.log(image);
        // => img
    },
    function (images) {
        console.log(images);
        // => [img, img]
    },
    false
);
```

Warning
-------

There is no retry after an error in image loading.


License
-------

The MIT License (see LICENSE file)
