_Note: This recommendation is a DRAFT for consideration of the MODX Governance Advisory Board._


To ensure that icons delivered with the MODX Next core are semantic, optimal, reliable, and accessible to all users the MODX Next core shall utilize progressively enhanced Icons. The core, and any themes packaged within, shall not utilize Icon Fonts.


_Note: FontAwesome 5.0 Pro has announced it will support SVG usage and over 1,000 new icons_


**Editor: JP de Vries**
**First publish draft: Nov 3, 2016**


## Goal of Recommendation 😃
To deliver icons used by the MODX Next manager in an accessible, performant, and standardized manner. To allow contributors creative freedom to add custom icons and control which icons are delivered.


## Relevant Recommendations
[DRAFT] Accessibility Mandate
[DRAFT] Bandwidth Considerations


## Relevant Issues
[Death to Icon Fonts #12771](https://github.com/modxcms/revolution/issues/12771)


## Recommendation
While Icon Fonts are convenient, in regards to accessibility, performance, optimization, and semantics they are a worst practice.

Even the new “Accessible FontAwesome 4.6” does not, and can not, escape the inaccessible nature of Icon Fonts.

When we speak of performance on the web, we often are referring to speed. The definition of performance has more to do with if, and how reliably, a given task is completed then how quickly it does so. Web Fonts are incredibly unreliable. Opera Mini, a mobile browsers which reached over 300 million global users, does not load web fonts at all. And it never will. Content Blockers such as Focus for iOS undetectably block web fonts. This means that while @fontface has a 93.21% caniuse score the actual number of users browsing with @fontface enabled is undetectably less. In comparison, SVG Icons have a 97.25% caniuse score, cannot be disabled, and can be used in conjunction with PNG fallbacks for 100% support. Web Fonts, and thus Icon Fonts, are not reliable.

While there are several strategies to loading web fonts, web fonts are by nature render blocking. This makes them costly as they delay the time until meaningful content is delivered. Additionally, it is cumbersome and uncommon to create custom Icon Fonts with only the icons you use. Shipping over 600+ icons to use a few dozen is non-optimal.

The `<i>` tag semantically represents oblique text. Not an icon. Icon Fonts are unsemantic. SVG tags are semantic, can be used in conjunction with `<title>`, and need no ARIA attributes.

MODX 2.x introduced a Grunt based workflow for automating front end assets. We can Grunt Icons into SVG Sprites giving us the freedom to combine icons from iconsets like FontAwesome along with custom icons into a single sprite file while also automating the creation of PNG fallbacks for 100% browser support. This means that rather than delivering all 600+ FontAwesome icons we can use the Grunt workflow to only include the icons we use. Modifying or adding new icons is as simply as dropping or editing .svg files in a folder.


It is recommended that icons are delivered Emoji first when possible and otherwise or based on system settings use the SVG `<use>` syntax with an optional PNG fallback as described in Grunt Icons into SVG Sprites Milestone 6. IE 9-11 do not support SVG `<use>` but there is a polyfill.

Purely decorative icons that are not relevant to semantics or internationalization may be delivered inaccessibly using CSS, web fonts, or anything else as they can safely remain invisible to the accessibility&nbsp;tree so long as they do not conflict with bandwidth considerations.
