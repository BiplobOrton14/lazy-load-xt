# Lazy Load XT jQuery plugin

---

## Table of Contents

- [About](#about)
- [Download / Install](#download-install)
- [Usage](#usage)
- [Demo](#demo)
- [Advanced initialization](#advanced-initialization)
- [Browsers with disabled JavaScript](#browsers-with-disabled-javascript)
- [Limitations](#limitations)
- [Options](#options)
- [Events](#events)
- [More than images](#more-than-images)
    - [`<iframe>`-embedded Videos (YouTube, Vimeo, etc.)](#iframe-embedded-videos-youtube-vimeo-etc)
    - [Support `<video>` tag](#support-video-tag)
- [Extendability](#extendability)
    - [Spinner](#spinner)
    - [Fade-in animation](#fade-in-animation)
    - [Hi-DPI (Retina) images](#hi-dpi-retina-images)
    - [AJAX](#ajax)
    - [Support of IE6/7](#support-of-ie6-7)
- [Addons](#addons)
    - [`<script>`-based tagging](#script-based-tagging)
    - [Responsive images](#responsive-images)
    - [Print](#print)
    - [Background image](#background-image)
    - [Deferred autoload](#deferred-autoload)
- [Example of page preparation in PHP](#example-of-page-preparation-in-php)
- [Version History](#version-history)
- [License](#license)


## About

Mobile-oriented, fast and extensible jQuery plugin for lazy loading of images/videos with build-in support of
jQueryMobile framework.

Currently tested in IE 6-11, Chrome 1-31, Firefox 1.5-27.0, Safari 3-7, Opera 10.6-18.0, iOS 5-7, Android 2.3-4.4,
Amazon Kindle Fire 2 and HD 8.9.

**Required jQuery 1.7+ or Zepto 1.0+.**


## Download / Install

<table>
  <tbody>
    <tr>
      <td>Dev version:</td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.js">jquery.lazyloadxt.js</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.extra.js">jquery.lazyloadxt.extra.js</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.simple.js">jquery.lazyloadxt.simple.js</a></td>
    </tr>
    <tr>
      <td>Minified version:</td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.min.js">jquery.lazyloadxt.min.js</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.extra.min.js">jquery.lazyloadxt.extra.min.js</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.simple.min.js">jquery.lazyloadxt.simple.min.js</a></td>
    </tr>
  </tbody>
</table>

Addons:

<table>
  <tbody>
    <tr>
      <td><a href="#script-based-tagging-of-lazy-loaded-elements">script-based tagging of lazy loaded elements</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.script.js">[jquery.lazyloadxt.script.js</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.script.min.js">jquery.lazyloadxt.script.min.js</a></td>
    </tr>
    <tr>
      <td><a href="#responsive-images-and-srcset">Responsive images and srcset</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.srcset.js">jquery.lazyloadxt.srcset.js</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.srcset.min.js">jquery.lazyloadxt.srcset.min.js</a></td>
    </tr>
    <tr>
      <td><a href="#print">Print</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.print.js">jquery.lazyloadxt.print.js</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.print.min.js">jquery.lazyloadxt.print.min.js</a></td>
    </tr>
    <tr>
      <td><a href="#background-image">Background image</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.bg.js">jquery.lazyloadxt.bg.js</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.bg.min.js">jquery.lazyloadxt.bg.min.js</a></td>
    </tr>
    <tr>
      <td><a href="#deferred-load">Deferred load</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.autoload.js">jquery.lazyloadxt.autoload.js</a></td>
      <td><a href="https://raw.github.com/ressio/lazy-load-xt/master/dist/jquery.lazyloadxt.autoload.min.js">jquery.lazyloadxt.autoload.min.js</a></td>
     </tr>
  </tbody>
</table>

Install and manage Lazy Load XT using [Bower](http://bower.io/)

    $ bower install lazyloadxt

Install and manage using [NPM](https://npmjs.org/)

    $ npm install lazyloadxt

Get full snapshot of Lazy Load XT: [lazy-load-xt-master.zip](https://github.com/ressio/lazy-load-zt/archive/master.zip)

If you have any feature to request or bug to report please use
[GitHub issues]( https://github.com/ressio/lazy-load-xt/issues).


## Usage

First of all it's necessary to load jQuery and Lazy Load XT script. There are three versions of Lazy Load XT:

1. `jquery.lazyloadxt.js`, standard version for lazy loading of images only.

2. `jquery.lazyloadxt.extra.js`, version with included video addon for lazy loading of both images and videos.

3. `jquery.lazyloadxt.simple.js`, version of minimal size with excluded support of on* handlers, lazy* events,
    `blankImage` option and addons.

To make media elements (`img`, `video`, `source`, `iframe`) to be lazy loaded, rename `src` attribute to `data-src`.
It is highly recommended to set `width` and `height` attributes. Optionally you can add a placeholder `src` to bypass
HTML validators:

    ```html
    <script src="jquery.js"></script>
    <script src="jquery.lazyloadxt.js"></script>

    <img data-src="lazy.jpg" width="100" height="100">
    ```


## Demo

Demo: [ressio.github.io/lazy-load-xt](http://ressio.github.io/lazy-load-xt)


## Advanced initialization

There are several possible ways to initialize elements if auto initialization doesn't suit you:

1. `$(container).lazyLoadXT();`
2. `$(container).lazyLoadXT(selector);`
3. `$(img.selector).lazyLoadXT();`

Note: don’t forget to disable auto initialization with `$.lazyLoadXT.autoInit=false;` if you like to use manual
initialization of all elements.


## Browsers with disabled JavaScript

As JavaScript may be disabled in the browser (e.g. it may be a feature phone with limited javascript support or browser
with Noscript addon), it is usually recommended to add a fallback image in `<noscript>` tag, mark initial image with
`class="lazy"` attribute and hide it using CSS (otherwise browsers with disabled javascript will display both images).
Lazy Load XT plugin removes this class (`classNojs` option) at image initialization. So, final code should be like:

    ```css
    img.lazy {
      display: none;
    }
    ```

    ```html
    <img class="lazy" data-src="lazy.jpg" width="100" height="100">
    <noscript><img src="lazy.jpg" width="100" height="100"></noscript>
    ```

We recommend to keep the order of attributes in both `<img>` tags, because of such a code will be effectively gzipped.

Alternative approach is based on tagging images/videos with `<script>` tag. It is realized using
`jquery.lazyloadxt.script.js` addon and is described in [corresponding addon’s section](#script-based-tagging)
(note that this approach is experimental and currently is not compatible with AJAX).


## Limitations
Unlike other lazy loading plugins, Lazy Load XT uses global collection of "lazy" elements and shared settings. This
allows to get better performance, but in most cases it is impossible to have two or more containers with independent
set of settings.


## Options

The plugin is very extensible and supports a lot of options that are stored in $.lazyLoadXT object:

    ```javascript
    $.extend($.lazyLoadXT, {
      edgeY:  200,
      srcAttr: 'data-src'
    });
    ```

You can either create this object before loading of `jquery.lazyloadxt.js`, or extend it after loading (but before
jQuery's `ready` event).

* **autoInit**: auto initialization of the plugin, that is processing of all elements matching `selector` selector in
  jQuery's `ready` event, if it is disabled you have to do such initialization manually as explained in [Advanced
  initialization](#advanced-initialization) section (default `true`)
* **selector**: selector for elements that should be lazy-loaded (default `'img'`)
* **srcAttr**: attribute containing actual `src` path, see example below in [Hi-DPI (Retina) images]
  (#hi-dpi-retina-images) section (default `'data-src'`)
* **classNojs**: class name used to hide duplicated element (outside of `<noscript>` tag) in the case of disabled
  JavaScript in browser, the plugin removes this class to make images visible (default `'lazy'`)
* **blankImage**: blank image for used until actual image is not loaded (default is transparent 1x1 gif image in
  data-uri format `'data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7'`)
* **edgeY**: expand visible page area (viewport) in vertical direction by specified amount of pixels,
  so that elements start to load even if they are not visible, but will be visible after scroll by `edgeY` pixels
  (default `0`)
* **edgeX**: expand visible page area in horizontal direction by specified amount of pixels (default `0`)
* **throttle**: time interval (in ms) to check for visible elements, the plugin uses it to speed up page work in the
  case of flow of page change events (default `99`)
* **visibleOnly**: added for compatibility with original
  [Lazy Load Plugin](https://github.com/tuupola/jquery_lazyload) by Mika Tuupola, being disabled this option forces
  the plugin to check element position only, but not to check that it is actually visible (default `true`)
* **loadEvent**: space-separated list of events when the plugin starts to found new elements matching `selector`
  (default `'pageshow'` to check AJAX-loaded content in jQueryMobile and to support backward navigation in iPhone)
* **updateEvent**: space-separated list of events when the plugin starts to check what elements are visible in
  current viewport (default `'load orientationchange resize scroll'`)
* **forceEvent**: space-separated list of events when the plugin starts to load all images independently of are
  they visible or not (default `''`)
* **oninit**: handler called when the plugin push elements into internal list of "lazy" elements,
  it may be either a function (DOM element is accessible using `this` object) or an object with `addClass` and/or
  `removeClass` properties (`addClass` is a space-separated list of class names that should be added to the elements,
  and `removeClass` contains class names that should be removed, `removeClass` has higher priority in the case of
  identical class names) (default `null`)
* **onshow**: handler called when an element appears in viewport area, it may be either a function or an object by
  analogy to `oninit` handler, see example below in [Spinner](#spinner) section (default `null`)
* **onload**: handler called when element is successfully loaded, it may be either a function or an object by analogy
  to `oninit` handler (default `null`)
* **onerror**: handler called when browser cannot load the element, it may be either a function or an object by analogy
  to `oninit` handler (default `null`)


## Events

Lazy Load XT plugin triggers following events for loading elements (just before call to corresponding handler in
`$.lazyLoadXT` options):

* `lazyinit`, the plugin push elements into internal list of "lazy" elements
* `lazyshow`, element appears in viewport area
* `lazyload`, element is successfully loaded
* `lazyerror`, browser cannot load the element
* `lazyloadall` (triggered on `window` element), internal list of lazy-loaded elements is empty, that is all elements
  are loaded or loading.

Unlike global handlers `$.lazyLoadXT`, using these events it's possible to assign individual handlers for media
elements.


## More than images

Images are not the only page elements that may be lazy loaded. Though default value for `$.lazyLoadXT.selector` is
`'img'`, you can append it by `iframe` to use lazy-loading for iframes, `video` for videos,
etc. Full list of supported tags include all tags with `src` attribute: `<audio>`, `<embed>`, `<frame>`,
`<iframe>`, `<img>`, `<video>`, `<input type="image">`.

We distribute special "extra" version of the plugin with additional code for lazyloading of `<video>` elements and
`<iframe>`ed YouTube videos. To use this version, it’s necessary to just load `jquery.lazyloadxt.extra.js` instead of
`jquery.lazyloadxt.js`.


### `<iframe>`-embedded Videos (YouTube, Vimeo, etc.)

Most of video hostings allow to embed videos as `<iframe>` elements (e.g. Youtube, Vimeo, DailyMotion, and even KickStarter)
and they may be lazy loaded in the way similar to images (by replacing `src` attribute by `data-src`):

    ```html
    <script src="jquery.lazyloadxt.extra.js"></script>
    ```

    ```html
    <iframe width="420" height="315" data-src="//www.youtube.com/embed/uOzO9O15gwI?rel=0" frameborder="0" allowfullscreen></iframe>
    ```

Demo: http://ressio.github.io/lazy-load-xt/demo/youtube-iframe.htm


### Support `<video>` tag

It is easy too, just replace `src` attribute by `data-src` and `poster` by `data-poster` (if exists).

    ```html
    <script src="jquery.lazyloadxt.extra.js"></script>
    ```

    ```html
    <video data-poster="/path/to/poster.jpg" width="320" height="240" controls>
      <source data-src="/path/to/video.mp4" type='video/mp4; codecs="avc1.42E01E, mp4a.40.2"'>
      <source data-src="/path/to/video.ogv" type='video/ogg; codecs="theora, vorbis"'>
    </video>

    <video data-src="/path/to/video2.mp4" width="320" height="240" controls></video>
    ```

Demo: http://ressio.github.io/lazy-load-xt/demo/video-html5.htm


## Extendability

Lazy Load XT plugin may be easily extended using `oninit`, `onshow`, `onload` and `onerror` handlers. Some examples are
listed below.


### Spinner

To display animated spinner while image is loading, you can set/reset CSS class in `onshow`/`onload` events:

    ```css
    /* CSS */
    .lazy-hidden {
      background:#eee url('/path/to/loading.gif') no-repeat 50% 50%;
    }
    ```

    ```javascript
    /* JS */
    $.extend($.lazyLoadXT, {
      onshow:  { addClass:    'lazy-hidden' },
      onload:  { removeClass: 'lazy-hidden' },
      onerror: { removeClass: 'lazy-hidden' }
    });
    ```

Demo: http://ressio.github.io/lazy-load-xt/demo/spinner.htm


### Fade-in animation

To add fade-in animation you can use following sample of `onload` event and CSS rules:

    ```css
    /* CSS */
    .lazy-hidden {
      opacity: 0;
    }
    .lazy-loaded {
      -webkit-transition: opacity 0.3s;
      -moz-transition: opacity 0.3s;
      -ms-transition: opacity 0.3s;
      -o-transition: opacity 0.3s;
      transition: opacity 0.3s;
      opacity: 1;
    }
    ```

    ```javascript
    /* JS */
    $.extend($.lazyLoadXT, {
      oninit: { addClass: 'lazy-hidden' },
      onload: { addClass: 'lazy-loaded', removeClass: 'lazy-hidden' }
    });
    ```

Demo: http://ressio.github.io/lazy-load-xt/demo/fadein.htm


### Hi-DPI (Retina) images

The code below allows you to use `data-src-3x` attribute for screens with 3x density (e.g. Samsung Galaxy S4),
`data-src-2x` for 2x density (e.g. iPhones 4+), and `data-src-1.5x` for 1.5x density (e.g. HTC Incredible S).

    ```javascript
    /* JS */
    (function($, dpr) {
      if (dpr>1)
        $.lazyLoadXT.srcAttr = 'data-src-' + (dpr > 2 ? '3x' : (dpr > 1.5 ? '2x' : '1.5x'));
    })(jQuery, window.devicePixelRatio || 1);
    ```

Demo: http://ressio.github.io/lazy-load-xt/demo/retina.htm

But in real world it's better to set `srcAttr` function and choose most suitable image URL among existing ones. Or set
`src` attribute in `lazyshow` event, like it is done in [Responsive images and srcset](#responsive-images-and-srcset)
addon.


### AJAX

If you use jQuery-based AJAX navigation and don't like to change existing AJAX callbacks,
you can apply lazy loading to new loaded content using `ajaxComplete` event. Note that `$.lazyLoadXT.loadEvent =
'pageshow ajaxComplete';` may not work correctly because of content is not added to the page at the time of
`ajaxComplete` event, that's why it's better to postpone initialization by `setTimeout`:

    ```javascript
    /* JS */
    $(window).on('ajaxComplete', function() {
      setTimeout(function() {
        $(window).lazyLoadXT();
      }, 50);
    });
    ```

Demo: http://ressio.github.io/lazy-load-xt/demo/ajax.htm


### Support of IE6/7

Lazy Load XT uses Data-URI-encoded transparent image for images outside of viewport (though this image may be visible
during fast page scroll or in print preview).  As IE 6 and 7 don't support Data-URI, you can change image for that
browsers:

    ```javascript
    /* JS */
    if (parseInt(navigator.userAgent.toLowerCase().split('msie')[1] || 8, 10) < 8)
        $.lazyLoadXT.blankImage = '//upload.wikimedia.org/wikipedia/en/d/d0/Clear.gif';
    ```


## Addons

Lazy Load XT may be easily extended to support other lazyloading-related things. Some examples are part of Lazy Load XT
project and listed below.


### Video

Support of video elements in extra version of Lazy Load XT is just an addon that is combined with base version of
the script. That is loading of

    ```html
    <script src="jquery.lazyloadxt.extra.js">
    ```

is identical to loading of

    ```html
    <script src="jquery.lazyloadxt.js">
    <script src="jquery.lazyloadxt.video.js">
    ```

Options

**$.lazyLoadXT.videoPoster** name of attribute with path to background image (by default `'data-poster'`).

Note: this addon append `iframe[data-src]` to `$.lazyLoadXT.selector`, so if you change `$.lazyLoadXT.srcAttr` option,
`selector` option should be altered properly.


### Responsive images

This addon allows to combine lazy loading and responsive images. Format of responsive images description is based
on [srcset attribute](http://www.w3.org/html/wg/drafts/srcset/w3c-srcset/) draft of HTML extension for adaptive images:

    ```html
    <script src="jquery.lazyloadxt.js">
    <script src="jquery.lazyloadxt.srcset.js">
    ```

    ```html
    <img data-srcset="image-hd.jpg 2x, image-phone.jpg 360w, image-phone-hd.jpg 360w 2x">

    <img data-srcset-base="image" data-srcset-ext=".jpg" data-srcset="-hd 2x, -phone 360w, -phone-hd 360w 2x">
    ```

If you like to have fallback image name to be `data-srcset-base`+`data-srcset-ext` (`image.jpg` in above example),
just put comma at the end of `data-srcset` tag: `data-srcset="-hd 2x, -phone 360w, -phone-hd 360w 2x,"`. Note that
this addon doesn't require browser to support `srcset` attribute draft.

Demo: http://ressio.github.io/lazy-load-xt/demo/srcset.htm


### Print

It is another issue of lazy loading: if user prints the page, only loaded images will be printed. This addon allows
to start loading of all images just after browser switch to print mode to render page. Note that this feature is
browser-dependent and currently it works correctly in IE only. In Chrome browser caches page state until user
change print options (printer, page orientation, margins, etc.). In Firefox and Safari addon works if user chooses
Print Preview before actual print (as they don't wait until images will be loaded). In Opera it works starting from
15.0 release (Presto didn't support both `beforeprint` event and matchMedia listeners).

    ```html
    <script src="jquery.lazyloadxt.js">
    <script src="jquery.lazyloadxt.print.js">
    ```

Demo: http://ressio.github.io/lazy-load-xt/demo/print.htm


### Background image

This addon allows you to use lazy-loading technique for background images of any tag.

    ```html
    <script src="jquery.lazyloadxt.js">
    <script src="jquery.lazyloadxt.bg.js">
    ```

    ```html
    <div data-bg="/path/to/image.png">...</div>
    ```

Above code set `background-image` CSS property to `/path/to/image.png` as soon `div` element becomes visible in
viewport area.

Options:

**$.lazyLoadXT.bgAttr** name of attribute with path to background image (by default `'data-bg'`). Note: attribute
should be set before loading of `jquery.lazyloadxt.bg.js` as it is used to alter `$.lazyLoadXT.selector` option.

Demo: http://ressio.github.io/lazy-load-xt/demo/bg.htm


### `<script>`-based tagging

The main problem of lazy loading is necessity to duplicate `<img>` tag in `<noscript>` wrapper to support browsers with
disabled JavaScript. As an alternative way, `jquery.lazyloadxt.script.js` addon allows to prepend tag `<img>` tag by
`<script>` in the following form (without duplicating and renaming `src` to `data-src`):

    ```html
    <script src="jquery.lazyloadxt.js">
    <script src="jquery.lazyloadxt.script.js">
    ```

    ```html
    <script>L()</script><img src="/path/to/image.jpg">

    <script>Lb()</script>
    <video>
      <source src="/path/to/video.mp4">
    </video>
    <script>Le()</script>

    <script>Lb('iframe')</script>
    <iframe src="/path/to/iframe.htm"></iframe>
    <script>Le()</script>
    ````

Here `L()` is function that should be called before self-closed tag like `<img>` and `<input>` (optional argument is
the tag name of lazy loaded element, by default `'img'`), `Lb()` should be called before other tags like `<video>`
and `<iframe>` (optional argument is the tag name of lazy loaded element, by default `'video'`), and `Le()` should be
called after corresponding closing tag.

Options:

**$.lazyLoadXT.srcsetAttr** name of attribute with responsive rules in srcset format,
**$.lazyLoadXT.srcsetBaseAttr** name of attribute for URL prefix,
**$.lazyLoadXT.srcsetExtAttr** name of attribute for URL suffix


Demo: http://ressio.github.io/lazy-load-xt/demo/script-tag.htm


### Deferred autoload

This is very simple addon (just few lines of code) that loads all images after specified time after page loading. That is loading of images
doesn't affect loading of CSSes and JavaScripts, and time to initial website rendering will be decreased.

    ```html
    <script src="jquery.lazyloadxt.js">
    <script src="jquery.lazyloadxt.autoload.js">
    ```

Options:

**$.lazyLoadXT.autoLoad** time interval between `load` page event and start of image loading (in ms, default is 50)

Demo: http://ressio.github.io/lazy-load-xt/demo/autoload.htm


## Example of page preparation in PHP

Instead of manipulating `<img>` tags directly (that is to replace `src` by `data-src`,
add `<noscript>` fallback image, etc.), it's possible to do html page postprocessing using [your favorite] language.
Here is example of how to do it using PHP:

    ```php
    /* PHP */
    function addLazyLoading($html) {
        $dom = new DOMDocument();
        if(!@$dom->loadHTML('<?xml encoding="UTF-8">' . $html)) // trick to set charset
	        return $html;
	    foreach($dom->childNodes as $item)
		    if($item->nodeType === XML_PI_NODE) {
			    $dom->removeChild($item);
			    break;
		    }
	    $dom->encoding = 'UTF-8';
	    $images = $dom->getElementsByTagName('img');
	    $blankImage = 'data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7';
	    for($i = $images->length - 1; $i >= 0; $i--) {
		    $node     = $images->item($i);
		    $clone    = $node->cloneNode();
		    $noscript = $dom->createElement('noscript');
		    $noscript->appendChild($clone);
		    $node->parentNode->insertBefore($noscript, $node);
		    $node->setAttribute('data-src', $node->getAttribute('src'));
		    $node->setAttribute('src',      $blankImage);
		    $node->setAttribute('class',    trim($node->getAttribute('class') . ' lazy'));
	    }
	    $newHtml = $dom->saveHTML();
	    if(!$newHtml)
		    return $html;
        return $newHtml;
    }
    ```

## Version History

- [**0.8.5**](https://github.com/ressio/lazy-load-xt/tree/0.8.5) (15.12.2013): New addons, “simple” version,
  `lazyloadall` event, slight reduce minified size
- [**0.8.4**](https://github.com/ressio/lazy-load-xt/tree/0.8.4) (12.12.2013): Fixed check of removed elements,
   support of `$.lazyLoadXT.videoPoster` parameter, additional examples in `src` (srcset polyfill, transparent
   placeholder for IE6/7)
- [**0.8.3**](https://github.com/ressio/lazy-load-xt/tree/0.8.3) (10.12.2013): Speed up initialization,
  new `forceEvent` option, additional examples of extendability in `/src` directory
- [**0.8.2**](https://github.com/ressio/lazy-load-xt/tree/0.8.2) (08.12.2013): Built-in support of videos in
 `jquery.lazyloadxt.extra.js`
- [**0.8.1**](https://github.com/ressio/lazy-load-xt/tree/0.8.1) (06.12.2013): Add support of `lazyinit`, `lazyshow`,
 `lazyload`, and `lazyerror` events
- [**0.8.0**](https://github.com/ressio/lazy-load-xt/tree/0.8.0) (05.12.2013): Initial release


## License

Lazy Load XT is licensed under the [MIT license](http://opensource.org/licenses/MIT)


[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/ce20db9f22e205daddcd819e106c8995 "githalytics.com")](http://githalytics.com/ressio/lazy-load-xt)