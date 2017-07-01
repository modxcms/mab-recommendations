_Note: This recommendation is a DRAFT for consideration of the MODX Governance Advisory Board._


To ensure that the MODX core is developed in accordance with globally adopted accessibility guidelines all new or updated code released with the MODX core must conform with the latest accessibility guidelines in addition to any guidelines accepted by the MODX Advisory Board.


**Editor: JP de Vries**
**First publish draft: Nov 3, 2016**


## Goal of Recommendation


To provide all MODX users the ability to author and publish the web.

 > “Following these guidelines will make content accessible to a wider range of people with disabilities, including blindness and low vision, deafness and hearing loss, learning disabilities, cognitive limitations, limited movement, speech disabilities, photosensitivity and combinations of these.”  
&emsp;&mdash;&emsp;[WCAG](https://www.w3.org/TR/WCAG20/)

## Relevant Recommendations
 - [Accessibile Setup DRAFT](https://github.com/modxcms/mab-recommendations/pull/14)
 - [Sync Endpoints DRAFT](https://github.com/modxcms/mab-recommendations/pull/14)
 - [Semantic Icons DRAFT](https://github.com/modxcms/mab-recommendations/pull/1)

## Relevant Material
 - [Themes Not Websites](https://www.joedolson.com/2016/08/themes-not-web-sites/) – some excellent points on why WCAG applies to site content, and not necessarily manager themes
 - [Drupal 8 Accessibility Features](https://twitter.com/johan_ramon/status/773150640403058689)

 ## Recommended Resources
  - [Accessibiilty Checklist](http://accessibility.voxmedia.com)
  
 ## Testing Software
 
 There is a vast array of accessibility testing software. To get you started, we&nbsp;recommend:
 
  - [axe-core Browser Extension](https://www.deque.com/products/axe-core/#aXeExtensions)
  
  ## Support Channels
  
   - [`#a11y` MODX Community Slack Channel](https://modxcommunity.slack.com/a11y)
   - [Accessibility on the MODX Forums](https://forums.modx.com/board/281/sig-accessibility)

## Recommendation
MODX enables site builders to not only create amazing experiences but also the creative freedom necessary to ensure the sites they create are accessible to all users. Unfortunately, to date the experience of building with MODX is not accessible to all users. Breaking changes allow the opportunity to adopt guidelines and ensure future major versions are truly&nbsp;accessible.

[Accessibility is water](https://modx.today/posts/2016/02/accessibility-is-water); we are all equally deserving of it. With breaking changes following this recommendation, we'll irrigate accessibility entirely throughout our diverse and global&nbsp;community.


> “Accessibility is a blueberry muffin. You can’t push the blueberries in afterwards.”  
&emsp;&mdash;&emsp;Cordelia McGee-Tubb


It is imperative that accessibility be considered first and foremost in the design and development process. This isn’t just to ensure that the end product is accessible to underrepresented groups but perhaps more importantly that it is user friendly and a better experience for everyone.

While MODX has acknowledged the importance of accessibility, to date the project hasn’t been able to define alone a path towards an accessible product. It would be unrealistic to expect MODX Contributors to become accessibility experts capable of following the latest accessibility success criteria and other best practices over night. This is why supporting documentation, examples, and human resources will be needed to make accessibility best practices accessible to contributors. Pun intended.

> “Accessibility allows us to tap into everyone’s potential.”  
&emsp;&mdash;&emsp;[@DebraRuh](https://twitter.com/akwyz/status/880712070496387072)

Members appointed by the MODX Advisory Board to an Accessibility Advisory Working Group act as Accessibility Advisors to the greater MODX&nbsp;Community. Core Contributors will be encouraged to consult and collaborate with Accessibility Advisors so that they are not surprised if a pull request is rejected due to lack of compliance with accessibility guidelines or additional guidelines adopted by the governance board.

We must not allow our quest for accessible code to result in making the process of authoring an approved Pull Request become less accessible to developers. In other words,  a novice to accessibility should feel as comfortable proposing recommendations and Pull Requests as an expert. If a contributor is unable to seek out or afford accessibility consultation an Accessibility Advisor will be appointed to them by the _________ in the form of _________________.

Accessibility guidelines clearly define requirements, but who decides if a Pull Request conforms to these guidelines? When architecting a structural building an architect designs the building, a builder constructs the building, and an inspector inspects the building to ensure it satisfies the appropriate building codes. The architect and the builder are expected to have knowledge of and follow building codes, but in the end it is the inspector who is the judge of if the building is structurally sound.

> “The best time to think about accessibility is in the beginning, the second best time is now.”  
&emsp;&mdash;&emsp;[@aaroni](https://twitter.com/aaroni/status/880132320220639232)

Front End Pull Requests must be approved by a certified MODX Accessibility Advisors who may not also be the author of the Pull Request being inspected. Back End Pull Requests that may impact accessibility on the front end shall also be inspected. For example, assuming the Synchronous Endpoints recommendation is accepted, interactions with the database such as accepting and processing user input must be supported both asynchronously and synchronously.

> “Every line of code written without #a11y in mind is a line that must be rewritten later. Pushing #accessibility down the road incurs development debt, increasing dev time and cost.”  
&emsp;&mdash;&emsp;[@mor10](https://twitter.com/mor10/status/879435792686264320)

While inspection at the end of the development process is needed, ideally accessibility review should be integrated into the forefront of the process. Accessibility Advisors should be available through support channels to collaborate with the community and development teams at any point in the development process.
