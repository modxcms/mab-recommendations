# 🌐 Accessible Setup ♿️

_Note: This recommendation is a DRAFT for consideration of the MODX Advisory&nbsp;Board._

The MODX Advisory Board recommends, in an effort to make an accessible first impression, the setup process will support the option to set accessibility preferences during the installation&nbsp;process.  
🔧🤘

**Editor: JP de Vries**
**First published draft: Nov 26, 2016**

## 🙏 Goals of Recommendation

  - To ensure that any accessibility preferences that may make the MODX Manager interface more accessible to users are accessible themselves during the installation setup&nbsp;process
  - ~~To allow Third Party Components to register preferences to the&nbsp;installer~~

## 📚 Relevant Recommendations

 - [Bandwidth Considerations](https://github.com/modxcms/mab-recommendations/pull/4)
 - [Accessibility Mandate](https://github.com/modxcms/mab-recommendations/pull/3)
 - [Progressive Icons Proposal](https://github.com/modxcms/mab-recommendations/pull/1)

## 🎯 Proof of Concepts
 - [MODX Setup](https://github.com/jpdevries/modx-setup#demo)
 - [Markup.tips Settings](https://markup.tips/settings.html#focus)
 - [MakeanIco Settings](http://makeanico.herokuapp.com/preferences)

## 📝 Recommendation
📓&ensp;At mod<strong>more</strong> we hired [Janita Top](https://www.meetup.com/Groningen-Frontend-Devs/members/148145182/) for some accessibility consulting. One of the things that stuck with me from her presentation was not to be too quick to celebrate victory. You may not have received any feedback about inaccessibility because if a someone can't use the site, they can't leave feedback to begin&nbsp;with.  
💡💥

_If a MODX user can not get to the System Settings page to update some settings or switch themes, that feature does not exist to&nbsp;them._

😃&ensp;Allowing users to set their preferences during the installation process will make for an accessible first impression of the MODX editing experience. Preferences like [contrast](https://markup.tips/settings.html#contrast), [font&ndash;size](https://markup.tips/settings.html#font-size), reduce animation, [font&ndash;family (choose a webfont)](https://markup.tips/settings.html#typeface), and even themes can be chosen during the installation&nbsp;process.

⌛️ This recommendation should not increase the amount of time it takes to install MODX. For example, these options could be hidden behind a button or&nbsp;`<summary>`.

📦&ensp;~~The core installation will ship with a default set of preferences configurable upon installation, but it is important that these preferences are not defined strictly by the core. Third Party Components (is that what we are calling Extras now?) should be able to register their own preferences that are accessible during&nbsp;installation.~~

🛠&ensp;Preferences should be able to be set as System, User, and/or `localStorage` Settings. This will allow MODX to be tailored to just your device, just your user, or system&nbsp;wide.

🎓&ensp;Someone who has a Masters Degree in Computer Science and just found out what MODX is 5 minutes ago, and is now trying to install it, is contextually a cognitively disabled MODX user. They don't know what MODX Extras are, let alone the right ones they need to install to get what they want done. It may take them days of trial and error and research to learn the MODX Extra ecosystem. The installation complete screen should allow users to specify what they will be building and automagically install the Extras they'll need. No longer will you need knowledge of what MODX Extras are what. You just tell MODX what you want to&nbsp;build.
