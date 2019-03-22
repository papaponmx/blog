# A hitchhikers guide to web images on 2019

The goals of this post is to give you some exposure to the current web capabilities and help you identify some opportunity areas for:

A few assumptions about you reading this post: 

* You are familiar with HTML.
* You know basic image formats like `jpg`, `png` and `svg`.
* You are somewhat familiar with CSS and enough have enough expertise to read, understand and implement the MDN documentation.

## Introduction

The web is evolving, fast. Nice to have features have become something you as a developer, are expected to be familiar with here are some that are common:

 * Internationalization (i18n).
 * Front End Routing.
 * Responsive web design.
 * Front End User Authentication.
 * SEO.
 * Page Speed Optimization.

## New features within the HTML spec

The HTML5 spec, is intended to serve a mobile web, you can think of it as two things a set of [HTML tags](https://www.w3schools.com/html/html5_new_elements.asp), and [several new APIs](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)


Let us revise some new tags and attributes one by one, after that I will add an example that uses all of these.

### `<picture>`

You can think of it as an `img` tag with more flexibility to display image resources. It allows us to provide higher-density versions of an image to high-[DPI](https://en.wikipedia.org/wiki/Dots_per_inch) displays. Let us see what it looks like, according to MDN:

>  The HTML <picture> element contains zero or more <source> elements and one <img> element to provide versions of an image for different display/device scenarios.

#### `<source>`

The HTML [`<source>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/source#attr-srcset) element specifies multiple media resources for the `<picture>`, the `<audio>` element, or the `<video>` element.

#### `srcset` attribute

This attribute is similar to `src`, but used to define multiple images `src`, there are many ways to implement this sources

Declare the **attribute once with multiple images and a src as a default**. Check original source at [webkit.org](https://webkit.org/demos/srcset/). 

```
<img 
  src="image-src.png" 
  srcset="image-1x.png 1x, 
          image-2x.png 2x,
          image-3x.png 3x, 
          image-4x.png 4x"
>
```

The other way is to declare multiple sources and within each have one `srcset`. You can see it in the example below. The main difference is that the second has a more specfic conditions for image displays.

**Putting it all together**:

[See it on Codepen](https://codepen.io/papapon/pen/EMOdWr?editors=1100)

```HTML
<picture>
  <source media="(max-width: 799px)" srcset="https://placekitten.com/200/300">
  <source media="(min-width: 800px)" srcset="https://placekitten.com/400/600">
  <img src="https://placekitten.com/600/800" alt="A cute black cat showing his love">
</picture>

```

## ~~New~~ relevant CSS properties

In case you did not know, spoiler alert, [CSS 4 does not exist](https://dev.to/olimpioadolfo/does-css4-exist-5ao4). Instead we have small increments being supported by modern browsers. Here are some properties that is good to be aware of:

### `object-position`

As the name suggests, `object-position`, defines the way in which an object is defined within a box. It is quite similar to [`background-position`](https://developer.mozilla.org/es/docs/Web/CSS/background-position). You can [see the code pen example in](https://codepen.io/robinrendle/pen/raGOOJ), thanks [@Robin Rendle](https://twitter.com/robinrendle).

### `image-rendering`

This property serves to tell the browser how it should render the image. The values describe the algorithm that will be implemented in order to scale the image, by the time of this writing, the possible values are:

* `auto`: Default value, the browser's algorithm will determine how to scale the image.  
* `crisp-edges`: It preserves contrast and edges in the image.
* `pixelated`: As the name suggests, the browser will keep it's pixelated style as the viewport grows.

You can see how this three images behave in [this example on Codepen](https://codepen.io/robinrendle/pen/XJPPMW).

Or check this [`image-rendering` applied to a QR code](https://codepen.io/robinrendle/pen/EaOJeq).

## Image formats

```HTML
<img alt="Apple iPhone 7 Plus, GSM Unlocked, 32GB - Rose Gold (Refurbished)" src="https://images-na.ssl-images-amazon.com/images/I/51gVm-dTdvL._AC_SY200_.jpg" class="product-image" height="200px" data-a-hires="https://images-na.ssl-images-amazon.com/images/I/51gVm-dTdvL._AC_SY400_.jpg">
```

## Lazy loading

Lazy loading images means that they are served slowly and it is avoided until it is necessary. 

When implemented, for the final user it usually means a smaller bundle served, faster loads and a better experience overall.

### Intersection Observer API

For starters, you might want to use the Intersection Observer API. 

> Simply put, the API provides users a way to observe given elements and monitor changes in their intersection with a given ancestor element, or the viewport itself.

If you use Gatsby, [Gatsby Link](https://www.gatsbyjs.org/docs/gatsby-link/) is already using it under the hood.

* [Intersection Observer API on MDN](https://developer.mozilla.org/es/docs/Web/API/Intersection_Observer_API).
* [Intersection Observer API support on caniuse.com](https://caniuse.com/#search=intersection).
* Great article: [Master the Intersection Observer API](https://www.hweaver.com/intersection-observer-single-page-navigation/).

For modern frameworks here are some npm packages you might want to look into:

* [React Loadable](https://github.com/jamiebuilds/react-loadable).
* [Vue Lazy Load](https://github.com/hilongjw/vue-lazyload).
* [React Lazy Load Image Component](https://github.com/Aljullu/react-lazy-load-image-component#readme)
* [Angular Lazy Loading Modules](https://angular.io/guide/lazy-loading-ngmodules).


## Skeletons

Even when you have lazy loading in place, user's internet speed might be slow or interrupted, even in urban areas, even if the user is not aware of it, so it is good to have something in place to the user to see. That's where skeletons come in place.

A skeleton is _a placeholder in a place which need waiting for loading_

You might have seen it before, this is what a skeleton looks like: 

![alt text](./img/skeleton_example.png "CSS skeleton example")

https://codepen.io/oslego/pen/XdvWmd

There are some npm packages you might use in order to implement this feature, but as a rule of thumb, let's use something simpler. 

### Introduce `:empty` pseudo-class

According to  MDN Docs:

> `empty` represents any element that has no children. Children can be either element nodes or text (including whitespace). Comments, processing instructions, and CSS content do not affect whether an element is considered empty.

So an skeleton can be as simple as

```CSS
/*
 * ...your styles
 */

.user-data:empty {
  background: rgba(130, 130, 130, 0.2); 
}
```

You can check an animated [Skeleton Screen with CSS](https://codepen.io/oslego/pen/XdvWmd) or [`:empty` at MDN Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/:empty).
  

## Automating strategies

## Further resources

 * [MDN Mobile Optimization](https://moz.com/learn/seo/mobile-optimization)
 * [Google's Mobile Testing Tool](https://search.google.com/test/mobile-friendly)
 * [Website Speed Test Image Analysis Tool](https://webspeedtest.cloudinary.com/)
 * [HTML5 Cheat Sheet](https://www.wpkube.com/html5-cheat-sheet/)
 * []()
 * []()
 * []()
 * []()
 * []()
 * []()
 * []()
 * []()
 * []()
 * []()

That's all folks, thanks to making it to the very end, keep on learning. 

Cheers.