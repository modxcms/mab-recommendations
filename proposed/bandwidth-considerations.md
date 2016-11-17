_Note: This recommendation is a DRAFT for consideration of the MODX Governance Advisory Board._


To be mindful of the cost users pay to access the MODX Next management experience the core shall effectively leverage the browser cache.


**Editor: JP de Vries**
**First publish draft: TBD**


## Goals of Recommendation


To make the MODX Next management experience more accessible and less expensive for our global user base. To optimize the page load times of the MODX Next manager across the web as a whole. To promote stability of the MODX Next manager experience. To add costly features and enhancements in a prgoressive manor so they can be opted out&nbsp;of.


## Relevant Recommendations
As bandwidth considerations is part of accessibility best practices, [DRAFT] Accessibility Mandate. This recommendation is proposed as a guideline accepted by the MODX Advisory Board and enforced by the Accessibility Mandate.


## Recommendation
Leverage the browser cache and stability of the progressively enhanced manager with the following practices:


Front End assets delivered with the core shall not be compressed or concatenated on the server side.
Front End assets delivered with the core shall first perform feature detection to test whether or not they are supported and not be loaded if they do not support the user’s environment.
Common Dependencies used by the core such as jQuery, React, AngularJS, etc shall conditionally be loaded from a common CDN with local fallbacks to preserve stability in the event the CDN is unreachable.
Extra Developers shall be encouraged, but not required, to perform feature detection to determine if a given asset has already been loaded.
Server Admins will be encouraged to optimize the delivery of MODX by enabling HTTPS (HTTP/2), GZIP compression, and far future reaching expiry dates


A great deal of research, testing, and debate went into the changes introduced in 2.5 that improved the stability and performance of the delivery of front end dependencies. The TL;DR is compressing and concatenating scripts on the server side is an anti optimization. This worst practice made the Manager experience less stable, as it was the cause of dozens of “white screen of death” issues.


The MODX Manager is not a website! The assets it loads vary from page to page, user to user, and change as Extras are enabled, installed, and disabled. From a bandwidth perspective, the Manager is the opposite of a web site. As proven in the Proof of Concept section, optimization that commonly apply to websites are anti-optimal when applied to the manager experience.




## Proof of Concept
Seen as how the pre-2.5 `compress_js` codebase was made under the assumption that developers should reduce the number of HTTP requests at all costs, and nothing else, it was frustrating to be asked to show numbers to prove that this was anti-optimal. That said, some interesting discoveries came from this process. For example, imagine this scenario:  

 - Let's say we have 350kb of scripts that when server side compress_js is used is all in a URL that contains a comma separated list of dependencies like this:
`/manager/min/index.php?f=/manager/assets/modext/core/modx.localization.js,/manager/assets/modext/util/utilities.js`
 - Everything is instead in it's own file and possibly not uglified at all (`compress_js` disabled)


With these user stories:
 - `compress_js` enabled
 - User visits a Resource edit page with `compress_js` enabled
 - We send them 350kb on script in a single file. `redactor.js` is one of the included files
 - User disabled Rich Text on the resource and refreshes the page
 - New URL, so we send them all the scripts again and leverage the cache for none of them even though all we are doing is sending them same scripts minus redactor


• User visits a Resource edit page with compress_js disabled
	• We send them 350kb or more of script in individual files. redactor.js is one of the included files
	• User disabled Rich Text on the resource and refreshes the page


Scenario A has a cache usage of 0%. Even though we are serving less data by disabling an Extra we resend all the bytes. The URL changes, the cache is purged. We couldn’t leverage the browser cache less if we tried. We couldn’t make the experience more expensive in terms of bandwidth if we tried.


Scenario B has a cache usage of 100%. Each dependency is its own request, and therefore own URL. The cache is leveraged as much as possible. Yes this means more HTTP requests and a possibly slower load time (probably not) over HTTP/1 but that only applies to the first page load. Once assets are cached, they are cached!





## Considerations
The cost of bandwidth varies greatly in different countries. For example, the average Brazilian works over 34 hours for every 500MB of bandwidth. By being considerate of bandwidth, we make the MODX site building more accessible to our global community.

![](http://j4p.us/0S0e2g1F2r0v/Image%202016-11-03%20at%2010.46.24%20PM.jpg)



## Examples
Loading from a CDN, with local fallbacks, only if feature detection is passed.

![](http://j4p.us/282s2A321a0r/Screen%20Shot%202016-11-03%20at%2010.47.31%20PM.png)
