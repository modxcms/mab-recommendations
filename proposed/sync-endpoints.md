_Note: This recommendation is a DRAFT for consideration of the MODX Governance Advisory Board._


To allow creative freedom in the MODX Next manager interface interactions with the database must support synchronous endpoints and may be progressively enhanced as asynchronous endpoints.


**Editor: JP de Vries**
**First publish draft: TBD**


## Goal of Recommendation


To allow unhindered creative freedom with how contributors and extra developers enhance the MODX Next manager experience. To provide a more stable and accessible manager experience that weathers the storms of the web and remains functional in the climate of script breakages.


## Relevant Recommendations
 - [DRAFT] Core Goals
 - [DRAFT] Accessibility Mandate


## Proof of Concept
Manage Users Matboard Lab


## Recommendation
As we trace our technology stack passed opinionated script frameworks and towards the universal language of the web we shed the obtrusive constraints of unstandardized tools while accepting and allowing ourselves to initially work within the unobtrusive constraints of authoring semantic, accessible, and enhanceable HTML documents. Working initially within the constraints of HTML first means challenging ourselves to achieve the base functionality of experiences with standard hypertext. Given that there is little to no asynchronous capabilities without scripts, we embrace the synchronous endpoints and standard form actions that allow otherwise static pages to be tied together though posting form data from one page to another before enhancing them as needed.


We’ve all seen the white screen of death issues with the MODX 2.x Manager. Often these are caused by scripts being malformed in the server-side compression process. If the scripts don’t make it to the client correctly, or they do make it but a collision or missing dependency causes a fatal error, or scripts are simply disabled, end users are left with a dysfunctional management experience. It is ironic that MODX, arguably the most suitable framework to author and serve HTML, is so dependent on JavaScript. With a state of the art backend that supports both synchronous and asynchronous endpoints, the MODX Next manager will not suffer from such an Achilles’ heel. Even if scripts break or fail to load, synchronous endpoints ensure nothing prevents the HTML interface from interacting with and successfully posting to the database.


A less opinionated API means more creative freedom for Extra Developers. For example, 2.x Extra Developers are forced to either work with, or cumbersomely around, ExtJS. HandyMan would be an example of working so far around ExtJS the /manager is sidestepped entirely. The absurd amount of !important CSS overrides required to hack the 2.5 Manager into being more mobile friendly are an example of forcefully working around ExtJS. A MODX Next API driven by semantic HTML and synchronous endpoints will never need to be avoided or side stepped by Extra developers. Anything that can be achieved with progressively enhancement will be achievable within the MODX Next manager.
