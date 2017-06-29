# 🌐 Accessible Setup ♿️

_Note: This recommendation is a DRAFT for consideration of the MODX Advisory&nbsp;Board._

The MODX Advisory Board recommends, in an effort to make an accessible first impression, a new more inclusive setup process will expose accessibility preferences during the installation&nbsp;process.  
🔧🤘

**Editor: JP de Vries**
**First published draft: Nov 26, 2016**

## 🙏 Goals of Recommendation

  - To ensure that any accessibility preferences that may make the MODX Manager interface more accessible to users are accessible themselves during the installation setup&nbsp;process
  - To reimagine the setup process to be more end&ndash;user friendly (more accessible and less technical&nbsp;language)

## 📚 Relevant Recommendations

 - [Bandwidth Considerations](https://github.com/modxcms/mab-recommendations/pull/4)
 - [Accessibility Mandate](https://github.com/modxcms/mab-recommendations/pull/3)
 - [Progressive Icons Proposal](https://github.com/modxcms/mab-recommendations/pull/1)

## 🎯 Proof of Concepts
 - [MODX Setup](https://github.com/jpdevries/modx-setup#demo)
 - [Screencast](https://vimeo.com/218397030)

## 📝 Recommendation
👤 If preferences to improve the accessibility of the MODX manager are managed through system settings, these preferences themselves might not be accessible to the user. Whether these preferences relate to contrast, font-size, reduced animations or fully optimised manager themes, if the user is unable to configure such options, those features do not exist to&nbsp;them. Therefore, accessibility preferences must also be configurable from an accessible&nbsp;setup. 

🎩 The most efficient user action is no action at all. The MODX setup intaller and default theme should "automagically" respond to relevant system level preferences such as high contrast mode, legibility preferences, and the presence of the `save-data`&nbsp;header. Users who are not familiar with system level preferences, or cannot access them, or for some reason choose to override them, benefit from also being able to manage these preference within&nbsp;MODX.

⌛️ This recommendation should not increase the amount of time it takes to install MODX. For example, these options could be hidden behind a button or&nbsp;`<summary>`.

🎓&ensp;Someone who has a Masters Degree in Computer Science and just found out what MODX is 5 minutes ago, and is now trying to install it, is contextually a cognitively disabled MODX user. They don't know what MODX Extras are, let alone the right ones they need to install to get what they want done. It may take them days of trial and error and research to learn the MODX Extra ecosystem. The installation complete screen should allow users to specify what they will be building and automatically install the Extras they'll need. No longer will you need knowledge of the MODX Extras ecosystem. You just tell MODX what you want to&nbsp;build.

📆&ensp;This recommendation target the first non&ndash;ExtJS version of&nbsp;MODX.
