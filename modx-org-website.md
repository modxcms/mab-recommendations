# MODX.org website

This is a MODX Advisory Board (MAB) recommendation for building a MODX.org website for the community and open source project.

* **Editors:** Christian Seel, Mark Hamstra, Gauke Pieter Sietzema, Romain Tripault, Rinze van der Brug, Mat Dave
* **First published draft:** 2017-04-18
* **Accepted:** Not yet voted.


## Goal of Recommendation

The current MODX.com website contains a significant amount of commercial and marketing related content about the company behind MODX. 

To better represent the open source project and community, the MODX Advisory Board recommends to build a separate MODX.org website, managed by the MAB, that focuses on the open source project. This website would be open source, allowing contributions from the community to share the work of maintaining the website. 


## Relevant Recommendations

No relevant recommendations.


## Recommendation

This recommendation outlines the requirements and content structure for a new MODX website dedicated to the open source project and community, to be hosted on MODX.org. 
MODX.org currently hosts a signup widget for the MODX community slack. This would be incorporated into the website instead.

### Requirements
* Open and transparent for anyone to contribute
* Covered by version control and workflow to allow contributions, possibly as a Git repository on GitHub
* Managed by the MODX Advisory Board

### Content structure
Navigation items are BOLD, other items are suggestions or notes about the (type of) content on that specific page.

* **Home**
    * Overview “What is MODX and why do I wanna use it?” from perspectives from each target group (editors, managers, developers)
    * Download buttons and release information & github link
    * Latest news (import from MODX.today)
    * Latest extra (new/updates)
    * Latest meetup / dates
    * Newsletter sign up
* **Download**
    * Individual subpages for each release including release highlights and full notes
* **Explore MODX**
    * section about the CMS and what it can do. Basically high-level documentation/marketing not unlike https://modx.com/get-modx. Should have some sections or filters for end users / front-end developers / back-end developers.
    * Logos from companies using MODX (if we find those - if we don't find any good ones, we won't show any)
    * Features
        * **Multi-site capabilities (contexts)**
        * **SEO**
        * **Extras**
        * **Security**
        * **Templating (tags, elements)**
        * **Architecture (technical stuff, xpdo, slim in the future etc)**
* **Community**
    * **Contribute**
        * Contributing code (covering git workflow, CLA)
        * Reporting issues and requesting features (covering process for doing so) 
        * Triaging issues
        * Testing pull requests
    * **Around the world**
        * Map showing user group locations
        * Listing meetup groups & dates (e.g. from meetup.com, linkedin)
        * How to organize
    * **MODX Advisory Board**
        * What is it?
        * Members
        * Recommendations
* **Get help**
    * **Documentation** ↗
        * docs.modx.com (later moved to docs.modx.org)
    * **Forum** ↗
        * forum.modx.org (discourse)
    * **Community Slack**
        * With email signup form to receive an invite via the API 
    * **Developer Directory**
        * free listing for every developer
    * **Commercial Support** ↗
        * modx.com/services/

### Future Enhancements
In the future, the MODX.org website could be extended to include other aspects of the MODX community, such as the documentation or the forum.  

The developer directory could be extended with paid, verified listings to fund hosting and other MODX community/MODX Advisory Board expenses. This would need some formal legal organisation or structure.

### To Dos after acceptance
* Start a "modx.org" working group
* Create a public repository at github.com/modxcms/modx.org and add MAB members as Collaborators
* Explore hosting options
* Define tech-stack
* Define rules for merging PRs / new content
* Wireframing & Screendesign
* Templating & Integration
