_Note: This recommendation is a DRAFT for consideration of the MODX Governance Advisory Board._


To be mindful of the cost users pay to access the MODX Next management experience the MODX distribution shall effectively leverage the browser&nbsp;cache.


**Editor: JP de Vries**
**First publish draft: Nov 3, 2016**


## Goals of Recommendation


 - To make the MODX Next management experience less expensive and thus more accessible to our global user&nbsp;base
 - To optimize the page load times of the MODX Next manager across&nbsp;installations
 - To promote stability of the MODX Next manager&nbsp;experience
 - To add costly features and enhancements in a progressive&nbsp;manor


## Relevant Recommendations
As bandwidth considerations are part of accessibility best practices, [[DRAFT] Accessibility Mandate](https://github.com/modxcms/mab-recommendations/pull/3). This recommendation is proposed as a guideline accepted by the MODX Advisory Board and enforced by the Accessibility&nbsp;Mandate.

The [Progressive Icons Purposal](https://github.com/modxcms/mab-recommendations/pull/1) is also mindful of&nbsp;bandwidth.


## Recommendation
Leverage the browser cache and stability of the progressively enhanced manager with the following practices:


 - Front End (CSS, JS) dependencies shall not be concatenated or minified at&nbsp;runtime
 - Front End dependencies shall only be loaded if needed based&nbsp;on:
     - pass (or polyfills fail) feature&nbsp;detection
     - are not already&nbsp;loaded
 - Common Dependencies used in distribution shall conditionally be loaded from a common CDN with local fallbacks to leverage the cache while preserving stability in the event the CDN is&nbsp;unreachable
 - Server Admins will be encouraged to optimize the delivery of MODX by enabling HTTPS (HTTP/2), GZIP compression, far future reaching expiry dates
 - Service Worker(s) will be used to cache sticky cachebusted&nbsp;assets
 - Extra Developers shall be encouraged, but not required, to follow this&nbsp;recomemendation 

## Considerations
The cost of bandwidth varies greatly in different countries. For example, the average Brazilian works over 34 hours for every 500MB of bandwidth. By being considerate of bandwidth, we make building with MODX more accessible to our global community.

![](http://j4p.us/0S0e2g1F2r0v/Image%202016-11-03%20at%2010.46.24%20PM.jpg)



## Examples
An HTML pattern to load from a CDN, with local fallbacks, only if feature detection is passed and the dependency is not already&nbsp;loaded:

```html
<script>
  const doEnhancments = document.addEventListener ? true : false, // there is no reason to load scripts we know will break
  useCDN = true; // imagine this is a system/user setting
</script>

<!-- NOTE: change these to load the .min in production. They are not only smaller filesize but have wildly different performance -->
<script defer>if(doEnhancments && !Redux && useCDN) document.write('<script src="//cdnjs.cloudflare.com/ajax/libs/redux/3.5.2/redux.min.js"><\/script>');</script>
<script defer>if(doEnhancments) try { Redux } catch (e) { document.write('<script src="assets/js/vendor/redux.js"><\/script>') }</script>

<script defer>if(doEnhancments && !React && useCDN) document.write('<script src="//cdnjs.cloudflare.com/ajax/libs/react/15.0.1/react.min.js"><\/script>');</script>
<script defer>if(doEnhancments) try { React } catch (e) { document.write('<script src="assets/js/vendor/react.js"><\/script>') }</script>

<script defer>if(doEnhancments && !ReactDOM && useCDN) document.write('<script src="//cdnjs.cloudflare.com/ajax/libs/react/15.0.1/react-dom.min.js"><\/script>');</script>
<script defer>if(doEnhancments) try { ReactDOM } catch (e) { document.write('<script src="assets/js/vendor/react-dom.js"><\/script>') }</script>

<script defer>if(doEnhancments && !ReactRedux && useCDN) document.write('<script src="//cdnjs.cloudflare.com/ajax/libs/react-redux/4.4.5/react-redux.min.js"><\/script>');</script>
<script defer>if(doEnhancments)try { ReactRedux } catch (e) { document.write('<script src="assets/js/vendor/react-redux.js"><\/script>') }</script>

<!-- put a version number or unique hash in filename to control and leverage browser cache -->
<script defer>if(doEnhancments) document.write('<script src="assets/js/mycomponent.1.0.0.min.js"><\/script>');</script>
```

A script based pattern to load dependencies lazyily and as/if needed:

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
 - [Lazy Load Scripts](https://github.com/jpdevries/developer-style-guide#lazy-load-scripts)
 - [Reluctant Loading](https://github.com/jpdevries/developer-style-guide#reluctant-loading)
