Installable Packages
################

Defines a set of guidelines on how MODX Extras should be selected for inclusion in the MODX setup. 

* **Editor:** Mark Hamstra
* **First published draft:** August 2017
* **Accepted:** Not yet voted.

## Goal of Recommendation

To make it easier for (primarily new) users to get started with MODX, it is being made possible to install packages directly from the setup. 

In order to, more or less objectively, determine which extras should be included in such a list of "Recommended" or "Suggested" extras, this recommendation provides guidelines that Extras can be tested against.

## Relevant Recommendations

N/a. 

## Recommendation

[Pull request #13472 adds the ability to install MODX Extras during the setup](https://github.com/modxcms/revolution/pull/13472), however in order to progress it and make it available to users, a list of suggested extras needs to be determined. 
  
As initial discussion on the pull request and recent board meetings have indicated, this is a difficult topic where a lot of personal preferences come into play. This recommendation provides a set of measurable guidelines that all suggested extras should meet.

### Guidelines

The goal of installing extras in the installer is to help (new) users get the tools they need to get started, not to replace the MODX Extras site. Not all extras have to be available from the setup. 

For an extra to be considered for inclusion, it should... 

1. have been publicly available on the official MODX extras site for at least 6 months
2. have at least 5000 downloads
3. be free, or have a free trial to install the Extra without requiring payment or providing payment information
4. provide documentation that meets the documentation requirements below. A link to the documentation must be included in the extras page.
5. have a publicly available bug tracker (or similar means to see known issues and submit reports)
6. be actively maintained, as described in the maintenance requirements below
7. have a clear and common use case that most MODX sites or apps need, which is not already covered by another suggested extra. 

It's important to note that extras go in and out of favour over time when competing extras come out, and it may be necessary to from time to time revisit extras that have previously been accepted.

### Documentation Requirements

Generally speaking, all documentation:

- must be available in at least English;
- must be available freely, so not hidden behind a paywall or login;
- must be predominantly in text form, with supporting media;

If the extra relies heavily on documentation in video or similar format, that media must be transcribed and provided as subtitles/closed captions in at least English.

For extras that provide one or more snippets, all snippets must be documented with:

- a clear description of what it is for and how it relates to other snippets
- how to call the snippet by showing a minimum snippet call example
- a list of available snippet properties with their default value
- for chunk-based templates, a list of available placeholders in each chunk. 

For extras that provide settings (or similar means of configuration), the setting name and description should be used to communicate their purpose from within the manager. Additionally, any setting that the average user would change also needs to be described in documentation. 


### Maintenance Requirements

Extras should have at least one active maintainer. This may be an individual person, or a company/vendor that has taken a maintenance role. 

As not all extras require weekly (or even yearly) patches, there is no minimum on the amount of activity to consider an extra to be actively maintained. Instead, whether an extra is considered to be maintained is based on answers to the following questions. 

- Who is (are) responsible for the extra, and have they accepted the responsibility to manage the project? 
- How are bug reports handled? Are they acknowledged and handled by the maintainer(s)? If the maintainer allows pull requests, are they reviewed and incorporated?
- Is there a dedicated place to get help with an extra that the maintainer(s) frequently help at?
