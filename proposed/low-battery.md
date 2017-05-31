# 🔋 Responding to Battery Levels

_Note: This recommendation is a DRAFT for consideration of the MODX Advisory&nbsp;Board._

The MODX Advisory Board recommends the Manager Interface respond to battery level for the first non&ndash;ExtJS&nbsp;Manager.

**Editor: JP de Vries**
**First published draft: Nov 19, 2016**

## 🙏 Goals of Recommendation

  - To allow responsive design into the MODX Manager in the form of responding to device battery&nbsp;level
  - Standardize three modes of CPU&nbsp;consumption

## 📚 Relevant Recommendations

 - [Bandwidth Considerations](https://github.com/modxcms/mab-recommendations/pull/4)
 - [Accessibility Mandate](https://github.com/modxcms/mab-recommendations/pull/1)

## 🎯 Proof of Concept
n/a

## 📝 Recommendation
> The Battery Status API, more often referred to as the Battery API, provides information about the system's battery charge level and lets you be notified by events that are sent when the battery level or charging status change. This can be used to adjust your app's resource usage to reduce battery drain when the battery is low, or to save changes before the battery runs out in order to prevent data loss.  
 [&emsp;&emsp;&mdash;&ensp;MDN](https://developer.mozilla.org/en/docs/Web/API/Battery_Status_API)

 Web Standards are constantly evolving and continue to allow for more app&ndash;like features. The next MODX interface will consist of web components that interface with the MODX API to `GET, PUT, POST, DELETE` data. What sets this apart from the 2.x Revolution interface is that:

  - core components shall be progressively enhanced
  - Freedom of the DOM, ExtJS no longer governs the document
  - components may be powered by any, or no, particular JavaScript framework or&nbsp;library

Tracing our tech stack back to web standards removes ExtJS only to add it back under the big tent of script freedom. Extra developers are free to use the JavaScript frameworks and libraries they choose. The API is not opinionated in this regard. This means that a futuristic interface could consist of components powered by different frameworks and libraries on the same&nbsp;page.

To keep an interface of freely created components consistent with the goals and recommendations of the MAB, Extra developers will be advised to architect their components to have three states of CPU&nbsp;efficiency:

 - Glutenous
 - Modest
 - Fasting

The explicit thresholds should be configurable through settings and accessibility preferences. For example, we may default to 20-40% levels triggering modest mode, but the threshold remains configurable on the user level. Extra developers are encouraged, but not required, to use the same thresholds as the core in their&nbsp;components.

**We'll optimize for low power and full power use cases alike by responding to dynamic power levels**. Instead of optimizing for a combination of the various power levels we can narrow optimizations down to the current power level. Our glutenous mode can be snappier with an abnormally frequent re&ndash;paint rate while low&ndash;power mode allows the interface to be accessed for more&nbsp;time.

## 🍻 Glutenous Mode
When devices have sufficient battery levels and/or are charging components are free to use all the CPU cycles they&nbsp;like.

## 🙂 Modest Mode
When low battery levels are detected components respond by limiting the amount of CPU cycles they consume. For example, if in glutenous mode a component hits the API every 15 seconds to check for updates it may respond by checking for updates less&nbsp;often.

Components in modest mode should also consider:
 - suspending transitions and animations
 - lazy&ndash;loading features that are not initially&nbsp;necessary
 - shedding costly CSS style effects
 - sending the `SAVE-DATA` header

along with any other considerable opportunities discovered when auditing and profiling CPU&nbsp;conservation.

## 😵 Fasting Mode
When critically low battery levels are detected components respond by entering a sleepy and lazily loaded state. For example, if the page was rendered prior to entering suspended mode, the component will switch from glutenous or modest mode to a suspended mode by ceasing to spend non&ndash;critical CPU cycles. A component in suspended mode does not hit the API or update the view unless it absolutely must. If the component is born suspended the component should be lazily loaded by progressively enhancing it from a HTML&nbsp;element. Once lazy loaded, the component responds to the current power level by launching in either modest or glutenous&nbsp;mode.
