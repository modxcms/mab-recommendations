_Note: This recommendation is a DRAFT for consideration of the MODX Governance Advisory Board._


To allow creative freedom in the MODX manager interface interactions with the database must support synchronous endpoints and may be progressively enhanced as asynchronous endpoints.


**Editor: JP de Vries**
**First publish draft: TBD**


## Goal of Recommendation


To allow unhindered creative freedom with how contributors and extra developers enhance the MODX manager experience. To provide a more stable and accessible manager experience that weathers the storms of the web and remains functional in the climate of script breakages.


## Relevant Recommendations
 - [DRAFT] Core Goals
 - [[DRAFT] Accessibility Mandate](https://github.com/modxcms/mab-recommendations/pull/3)


## Proof of Concept
 - [Manage Users Matboard Lab](https://github.com/jpdevries/manage-users#manage-users-lab)


## Recommendation
As we forgo opinionated script frameworks we allow ourselves to initially work within the unobtrusive constraints of authoring semantic, accessible, and enhanceable HTML documents. Working initially within the constraints of HTML&ndash;first means challenging ourselves to achieve basic functionality such as accepting user input and posting it to the server solely with semantic hypertext. We accept that there is little to no asynchronous capabilities without scripts and embrace the standard form actions. We'll `GET` and `POST` like it's&nbsp;1999.

We’ve all seen the white screen of death issues with the MODX 2.x Manager. Historically these were often caused by scripts being malformed during the server-side compression process. While 2.5 made the Manager Interface more reliable, it is still not immune to script breakages. If the scripts don’t make it to the client correctly, or they do make it but a collision or missing dependency causes a fatal error, or scripts are simply disabled, end users are left with a dysfunctional management experience. It is ironic that MODX, arguably the most suitable framework to author and serve HTML, is so dependent on JavaScript. With a state of the art backend that supports both synchronous and asynchronous endpoints, the MODX manager will weather the storms of script breakages. Even if scripts break or fail to load, synchronous endpoints guarantee a performant HTML interface which is ever capable of interacting with and successfully posting to the&nbsp;database. This ensures that anything that can be achieved by progressively enhancing web standards should be achievable within the MODX&nbsp;manager. With no more barriers or ExtJS leanring curves, we'll celebrate creative freedom when developing components for the Manager interface&nbsp;itself. 
