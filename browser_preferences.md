# Progressive Enhancement: Respecting web browser preferences in a post ES6 world

## Intro

After Google IO, and watching [a](https://www.youtube.com/watch?v=2KhRmFHLuhE) [few talks](https://www.youtube.com/watch?v=K2JzIUIHIhc), [about elevating](https://www.youtube.com/watch?v=c0oy0vQKEZE) [web capabilities](https://www.youtube.com/watch?v=-xZHWK-vHbQ), I got inspired. So here is [a bridge for you guys](https://en.wikipedia.org/wiki/The_Bridge_Builder).

## What is Progressive Enhancement?

In a nutshell, *Progressive Enhancement* is a philosophy for developing web applications and this are the principles:

* Basic content should be accessible to all web browsers.
* Basic functionality should be accessible to all web browsers.
* Sparse, semantic markup contains all content.
* Enhanced layout is provided by externally linked CSS.
* Enhanced behavior is provided by unobtrusive, externally linked JavaScript.
* End-user web browser preferences are respected.

An alternative to *PE* is *[Graceful Degradation](https://en.wikipedia.org/wiki/Fault_tolerance)*(GD). The difference is that PE goes from simple to complex while GD goes the other way around.

I've written [before](https://dev.to/papaponmx/in-praise-of-accessibility-outline-3m78) [about accessibility](https://dev.to/papaponmx/accessible-fonts-for-people-in-a-hurry-387) and will write another post for common heuristics for web development. 

More than persuading you to support IE or holding back on [CSS Grid](https://caniuse.com/#search=grid), my goal is to make you aware of new APIs we can use in order to comply with the last point on the list: _End-user web broser preferences are respected_.

## Respecting web browser preferences

Even if you are not aware of it, the browser exposes information about the user preferences, so let us walk through a few of them.

### Font system default

Another reason for using the system's default font is web performance, since there are no additional files to fetch from a server. There are three ways to accomplish this:

1. Using the `system-ui` value:
This is a value for font-family that represents the default user interface font. Except [for Firefox](https://bugzilla.mozilla.org/show_bug.cgi?id=1545745), it is supported by [most recent modern browsers](https://caniuse.com/#search=system-ui). 


2. Apply system fonts by calling them using `font-family`:
 I recommend hiding this behind a [feature query](https://developer.mozilla.org/en-US/docs/Web/CSS/@supports), as a fallback.

```css
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}
```

3. Using a polyfill.
Depending on your use case, this might be a last resource alternative. This is available as an npm package and this is the link: https://www.npmjs.com/package/font-family-system-ui

### Do Not track

This might be a controversial one. But the only fact that the user does not want you to,  should  be enough reason to stop monitoring their behavior. This is an opinion, but [privacy is a human right](https://en.wikipedia.org/wiki/Right_to_privacy).

The [Do Not Track API](https://developer.mozilla.org/en-US/docs/Web/API/navigator/doNotTrack) is [supported by modern browsers **expect Safari**](https://caniuse.com/#search=doNotTrack)

Here is what an implementation might look like:
```javascript
/**
 * "1" if DNT is enabled
 * "0" if the user opted-in for tracking
 * "unspecified" otherwise
 **/ 

if (navigator.doNotTrack === 0) {
	// Initialize Google Analytics scripts
} else if (!navigator.doNotTrack) {
	// Ask user if it is ok to track
} else {
	// DO NOT TRACK
}
```

Here is [ Do Not Track on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/doNotTrack).


### Default to user preferred language

Depending on your app, there might be an internationalization(i18n) implementation in your app. There is a way to default to user's language if supported, Instead of inferring it from their IP, location or your app preferences. 

https://developer.mozilla.org/en-US/docs/Web/API/NavigatorLanguage/language

### User `prefers-color-scheme`

`prefers-color-scheme` is a media feature that as the name implies, allows us to detect if the user has requested the system use a light or dark color theme.

This was [shipped on Firefox 67](https://hacks.mozilla.org/2019/05/firefox-67-dark-mode-css-webrender/), it is supported on Safari 12.1 but as the time of this writing, [support is still missing in most modern browsers](https://caniuse.com/#search=prefer).

Here is the link to [`prefers-color-scheme` on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme).

### User `prefers-reduced-motion`

Similar to the previous point, we can detect if the user prefers to have less animations. This might be due to accessibility concerns, or mere preference. I can see why this might be a concern if you have rich CSS animations, 3D Graphics or VR. 

The implementation in CSS is rather simple, here is what the code looks like: 

```css
.animation {
  animation: vibrate 0.3s linear infinite both; 
}

@media (prefers-reduced-motion: reduce) {
  .animation {
    animation: none;
  }
}
```

Further resources:

[`prefers-reduced-motion` on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion).
Here is a great article if you would like to look further into this: https://css-tricks.com/introduction-reduced-motion-media-query/


That's all folks, thanks for your taking the time to read this. You can read my other posts on [https://dev.to/papaponmx](https://dev.to/papaponmx) or say [hi on Twitter](https://twitter.com/papaponmx). 

Cheers.
