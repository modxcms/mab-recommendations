# MAB-06: A RESTful API & Steps to move away from ExtJS

Providing a 4-step process to decouple the MODX server-side code from the actions in the Manager interface, allowing development on the manager interface to take place without needing as much server-side knowledge. 

* **Editor:** Mark Hamstra
* **First published draft:** November 23, 2016
* **Accepted:** December 21, 2016 with 12 votes in favour

## Goal of Recommendation

Providing a clear path to develop a RESTful API for the MODX Manager, allowing the decoupling of ExtJS and connectors/processors. This will allow more rapid development of the MODX Manager frontend in a way that is independent of the backend code. 

## Relevant Recommendations

Synchronous Endpoints by John-Paul DeVries

## Recommendation

_Note: In the context of this recommendation, backend refers to the server-side PHP code primarily located in Connectors and Processors, whereas frontend is the manager interface currently built with ExtJS._

### Current Coupling of ExtJS and Processors

MODX 2.x uses a system of _Connectors_ and _Processors_ to provide data to the Manager. The connectors act as the endpoint for an AJAX request, where the action parameter points to a specific processor that needs to be executed. 

These processors are action-oriented and built to match the current features of the MODX Manager. Some examples of the current situation:

- To provide the data for the resource tree the `resource/getNodes` processor is used.
- The `element/getNodes` processor is used to populate the tree on the elements tab, which then triggers calls to the same processor with a node parameter set to template, plugin or snippet to retrieve the individual results.
- The `resource/update` processor is used for saving changes to a resource.
- System settings are retrieved through the `system/settings/getlist` processor. 

This action-based approach makes it necessary to have matching PHP code for each aspect or feature of the interface. It’s not possible to add a new feature to the ExtJS manager, for example to list resources in a certain resource group, without also writing new PHP code to provide the data or processing for that action. 

The result of this situation is that development of the manager frontend is largely dominated by developers that are comfortable with both ExtJS and PHP code. Server-side handling is limited to actions presented in ExtJS. It’s also not feasible to develop alternative interfaces that do not follow the exact same patterns without extensive back-end development.

### Decoupling the backend from the frontend 

To decouple the backend PHP code from the frontend manager interface, the interaction with the back-end should be standardized, and **resource-oriented** instead of **action-oriented**. Resource oriented means that there are endpoints for a resource, an object, which allows all actions to that resource. 

Transforming the current connector/processor approach into a RESTful API can provide that change. In a RESTful API the resources are central. The resources might be `plugin`, `user`, or `usergroup/members`, and each object can be retrieved or manipulated through GET, POST, PUT and DELETE requests. This allows full CRUD (Create, Read, Update and Delete) actions on an object.

Decoupling the backend from the frontend will allow backend developers to focus on what they do best, while frontend developers and designers can collaborate to build innovative manager interfaces without also requiring a backend developer. 

### Steps towards a RESTful API

The move towards a RESTful API can be started today, with the current version of MODX, and further integrated into the core in future versions. By starting this process before MODX 3 as a standalone extra, it can be adopted early to make the transition easier.

This proposal consists of 4 steps.

1. Document and specify the full API. This includes defining each of the resources and endpoints, the parameters they accept, and return structure/values. The specification may include details on authentication and other requirements for spec-compliant APIs. 

2. Develop the RESTful API. Based on the API Specification from step 2, the RESTful API can be developed as a standalone extra, distributed freely through MODX.com under the MIT or GPL license.

3. If determined necessary at the time, develop an ExtJS wrapper. This wrapper would translate AJAX requests coming from ExtJS targetting a connector/processor, to a GET, POST, PUT or DELETE request to the RESTful API. This would allow the MODX Manager to interact with the RESTful API without a full rewrite.

4. Incorporate the RESTful API into the MODX Core. This should be done in a breaking release (e.g. 3.0 or 4.0), accompanied by other changes to the MODX Manager. The no-longer used connectors and processors can then be deprecated or removed from the code. 

### New Manager Interface

This recommendation, nor the proposed RESTful API, does not define what framework or library (if any) should be used in a new manager interface, or what it should do. This is on purpose.
 
When the RESTful API is available (step 2), designers and frontend developers can collaborate on a completely rewritten manager interface, which uses the RESTful API for interacting with the backend. Depending on the outcome of such a collaboration, step 3 may no longer be necessary.

Should the synchronous form-based interaction recommendation be accepted, a server-side wrapper for the API could be developed that handles form-based interactions. 

### Breaking Changes & Other Considerations

This is a big change that will contain breaking changes.

Removing the connectors and processors from the MODX core will have the biggest impact, unless an alternative MODX manager is implemented at the same time. The `$modx->runProcessor` method would also become obsolete, and third party extras are likely to be affected. Some breaking changes may be avoided by mapping old features to new code. However, by releasing the API early, it is hoped that many developers will future-proof their third party extras ahead of time. 

Any client-side extra that extends or mimics core manager functionality may be affected by step 3 or 4 of the proposed process. This also includes custom resource classes, which currently depend on extended processors to function fully. These breaking changes may be harder to resolve, requiring further development. 

Another consideration of providing a full RESTful API is that, with proper authentication mechanisms and permissions, it could also be used in frontend (site/user-facing) code. When the WordPress community worked on the WP API initiative, the ability to retrieve information from the site in the front-end was promoted as one of its biggest benefits. This benefit would also be available to MODX following the development of a RESTful API, though less so compared to WordPress given the ease of extracting content from MODX through other pre-existing means.
