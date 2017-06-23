_Note: This recommendation is a DRAFT for consideration of the MODX Governance Advisory Board._


To ensure that the MODX core is developed in accordance with globally adopted accessibility guidelines all new or updated code released with the MODX core must conform with the latest accessibility guidelines in addition to any guidelines accepted by the MODX Advisory Board.


**Editor: JP de Vries**
**First publish draft: Nov 3, 2016**


## Goal of Recommendation


To provide all MODX users the ability to author and publish the web.


## Relevant Recommendations
 - [DRAFT] Core Goals


## Relevant Material
[Themes Not Websites](https://www.joedolson.com/2016/08/themes-not-web-sites/) – some excellent points on why WCAG applies to site content, and not necessarily manager themes
[Drupal 8 Accessibility Features](https://twitter.com/johan_ramon/status/773150640403058689)


## Recommendation
MODX enables site builders to not only create amazing experiences but also the creative freedom necessary to ensure the sites they create are accessible to all users. Unfortunately, to date the site building experience itself is not accessible to all users. MODX Next allows for breaking changes and with this opportunity we can adopt guidelines to ensure anything released with the MODX Next core is truly accessible.


> “Accessibility is a blueberry muffin. You can’t push the blueberries in afterwards.” – Cordelia McGee-Tubb


It is imperative that accessibility be considered first and foremost in the design and development process. This isn’t just to ensure that the end product is accessible to underrepresented groups but perhaps more importantly that it is user friendly and a better experience for everyone.


> “Accessibility is a fundamental design problem, not a liability problem” – David Storey


While MODX has acknowledged the importance of accessibility, to date the project hasn’t been able to accurately define accessibility – let alone a path towards it. It would be unrealistic to expect MODX Contributors to become accessibility experts capable of following the latest accessibility success criteria and other best practices over night. This is why supporting documentation, examples, and human resources will be needed to make accessibility best practices accessible to contributors. Pun intended.


Core Contributors will be encouraged to consult and collaborate with Accessibility Advisor within the MODX Community so that they are not surprised if a pull request is rejected due to lack of compliance with accessibility guidelines or additional guidelines adopted by the governance board.


We must not allow our quest for accessible code to result in making the process of authoring an approved Pull Request become less accessible to developers. In other words,  a novice to accessibility should feel as comfortable proposing recommendations and Pull Requests as an expert. If a contributor is unable to seek out or afford accessibility consultation an Accessibility Advisor will be appointed to them by the _________ in the form of _________________.


Accessibility guidelines clearly defines requirements, but who decides if a Pull Request conforms to these guidelines? When architecting a structural building an architect designs the building, a builder constructs the building, and an inspector inspects the building to ensure it satisfies the appropriate building codes. The architect and the builder are expected to have knowledge of and follow building codes, but in the end it is the inspector who is the judge of if the building is structurally sound.


Front End Pull Requests must be approved by a certified MODX Accessibility Advisors who may not also be the author of the Pull Request being inspected. Back End Pull Requests that may impact accessibility on the front end shall also be inspected. For example, assuming the Synchronous Endpoints recommendation is accepted, interactions with the database such as accepting and processing user input must be supported both asynchronously and synchronously.

While inspection at the end of the development process is needed, ideally accessibility review should be integrated into the forefront of the process. Accessibility Advisors should be available to collaborate with the community and development teams at any point in the development process.


_NOTE: How are Accessibility Advisors approved? By the board? By an appointed Accessibility Ambassador? By a community committee?_
