Convert the Documentation to Markdown
################

To increase community involvement and to make it easier to manage, the official documentation should be changed to markdown-based structure, backed by a public GitHub repository.

* **Editor:**  Matthew (matdave) Jones
* **First published draft:** 2017-04-13
* **Accepted:**  Not yet voted.

## Goal of Recommendation

To make the [official MODX documentation](https://docs.modx.com/) easier to manage.

## Relevant Recommendations

No relevant recommendations.

## Recommendation

Currently to edit the MODX Documentation, a separate user account that can only be used for the documentation is necessary to make changes. This results in a limited number of editors keeping the documentation up to date. There is no approval workflow: anyone with access can remove or make changes, without any verification or process to ensure the changes are correct. There's also no (publicly visible) history. 

To improve the documentation, it should be moved to a Markdown format, hosted on a public GitHub repository. Daux.io, or a similar tool, could be used to build and serve the documentation. 

Using Markdown in a public GitHub repository achieves the following:

- Editors do not require a separate user account only for the documentation. A GitHub account is needed, which does not appear to be prohibitive based on activity on the [documentation issues repository](https://github.com/modxcms/Docs/issues) or the primary [Revolution repository](https://github.com/modxcms/revolution).
- Puts in place an approval workflow through pull requests. This allows anyone to propose changes, including directly from the GitHub interface. Anyone can comment on pull requests for review, while a limited group of trusted individuals would be given access to merge and push changes.  
- Git keeps a full, detailed history of changes, which is browsable on GitHub. 
- Markdown is a flat-file format that is easy to process into other formats. This would allow future enhancements to the way content is displayed or distributed. 

Combined, these improvements are expected to result in more community activity in keeping the documentation up-to-date and to improve it over time.

As moving the documentation into a markdown format is a big project, a Working Group should be formed to coordinate the effort.