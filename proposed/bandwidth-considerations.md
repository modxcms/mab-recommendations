_Note: This recommendation is a DRAFT for consideration of the MODX Governance Advisory Board._


To be mindful of the cost users pay to access the MODX Next management experience the core shall effectively leverage the browser cache.


**Editor: JP de Vries**
**First publish draft: Nov 3, 2016**


## Goals of Recommendation


To make the MODX Next management experience more accessible and less expensive for our global user base. To optimize the page load times of the MODX Next manager across the web as a whole. To promote stability of the MODX Next manager experience. To add costly features and enhancements in a progressive manor so they can be opted out&nbsp;of.


## Relevant Recommendations
As bandwidth considerations is part of accessibility best practices, [[DRAFT] Accessibility Mandate](https://github.com/modxcms/mab-recommendations/pull/3). This recommendation is proposed as a guideline accepted by the MODX Advisory Board and enforced by the Accessibility&nbsp;Mandate.


## Recommendation
Leverage the browser cache and stability of the progressively enhanced manager with the following practices:


Front End (CSS, JS) assets delivered with the core shall not be compressed or concatenated on the server side.
Front End assets delivered with the core shall first perform feature detection to test whether or not they are supported and not be loaded if they do not support the user’s environment.
Common Dependencies used by the core such as jQuery, React, Angular, etc shall conditionally be loaded from a common CDN with local fallbacks to preserve stability in the event the CDN is unreachable.
Extra Developers shall be encouraged, but not required, to perform feature detection to determine if a given asset has already been loaded.
Server Admins will be encouraged to optimize the delivery of MODX by enabling HTTPS (HTTP/2), GZIP compression, far future reaching expiry dates, and using a service worker to cache sticky assets of their web component(s).

## Considerations
The cost of bandwidth varies greatly in different countries. For example, the average Brazilian works over 34 hours for every 500MB of bandwidth. By being considerate of bandwidth, we make the MODX site building more accessible to our global community.

![](http://j4p.us/0S0e2g1F2r0v/Image%202016-11-03%20at%2010.46.24%20PM.jpg)



## Examples
Usint an HTML pattern to load from a CDN, with local fallbacks, only if feature detection is passed.

![](http://j4p.us/282s2A321a0r/Screen%20Shot%202016-11-03%20at%2010.47.31%20PM.png)

Use a script based pattern to load dependencies lazyily and as/if needed:

```js
import lazyLoadScript from 'lazyload-script';

const promises = [];

if(!React) promises.push(
  // try to load React from a CDN, fallback to a local copy
  lazyLoadScript("https://cdnjs.cloudflare.com/ajax/libs/react/15.4.2/react.min.js", "react.15.4.2.min.js").catch((err => (
    lazyLoadScript(`./js/vendor/react.15.4.2.min.js`, "react.15.4.2.min.js")
  )))
);

if(!ReactDOM) promises.push(
  // try to load React DOM from a CDN, fallback to a local copy
  lazyLoadScript("https://cdnjs.cloudflare.com/ajax/libs/react/15.4.2/react-dom.min.js", "react-dom.15.4.2.min.js").catch((err => {
    lazyLoadScript(`./js/vendor/react-dom.15.4.2.min.js`, "react-dom.15.4.2.min.js")
  }))
);

if(!Redux) promises.push(
  // try to load Redux from a CDN, fallback to a local copy
  lazyLoadScript("https://cdnjs.cloudflare.com/ajax/libs/redux/3.6.0/redux.min.js", "redux.3.6.0.min.js").catch((err => {
    lazyLoadScript(`./js/vendor/redux.3.6.0.min.js`, "redux.3.6.0.min.js")
  }))
);

if(!ReactRedux) promises.push(
  // try to load React Redux from a CDN, fallback to a local copy
  lazyLoadScript("https://cdnjs.cloudflare.com/ajax/libs/react-redux/5.0.3/react-redux.min.js", "react-redux.5.0.3.min.js").catch((err => {
    lazyLoadScript(`./js/vendor/react-redux.5.0.3.min.js`, "react-redux.5.0.3.min.js")
  }))
);

Promise.all(promises).then(() => {
  // React, React DOM, Redux, and React Redux are ready. woohoo!
});
```

**See Also**

 - [Code Splitting](https://github.com/jpdevries/developer-style-guide#code-splitting)
 - [Lazy Load Scipts](https://github.com/jpdevries/developer-style-guide#lazy-load-scripts)
 - [Reluctant Loading](https://github.com/jpdevries/developer-style-guide#reluctant-loading)
