# A RESTful API & Steps to move away from ExtJS

Note: This recommendation is a DRAFT for consideration of the MODX Advisory Board. 

Providing a 4-step process to decouple the MODX server-side code from the actions in the Manager interface, allowing development on the manager interface to take place without needing as much server-side knowledge. 

Editor: Mark Hamstra

First published draft: Not yet reviewed/published.

## Goal of Recommendation

The goal of this recommendation is to offer a set of steps we can start taking right now, in order to move away from ExtJS 3.x in a future release. It does this by moving away from the current connectors and processors, which are heavily opinionated towards the actions in the manager and ExtJS 3.x approaches, and instead providing a RESTful API that can be used by any framework or library, including a wrapper for the existing ExtJS code. 

## Relevant Recommendations

Synchronous Endpoints by John-Paul DeVries

## Recommendation

_In the context of this recommendation, backend refers to the server-side PHP code, whereas frontend is the manager interface._

### How MODX is tied to ExtJS currently

MODX uses a system of Connectors and Processors to provide data to the Manager. The connectors act as the endpoint for an AJAX request, where the action parameter points to a specific processor that needs to be executed. 

These processors are very action-oriented and tied to the current features of the MODX Manager. Some examples of the current situation:

- To provide the data for the resource tree the `resource/getNodes` processor is used.
- The `element/getNodes` processor is used to populate the tree on the elements tab, which then triggers calls to the same processor with a node parameter set to template, plugin or snippet to retrieve the individual results.
- The `resource/update` processor is used for saving changes to a resource.

This action-based approach makes it necessary to have PHP code for each aspect or feature of the interface. It’s not possible to add a new feature to the ExtJS manager, for example to list resources in a certain resource group, without also writing new PHP code to provide the data or processing for that action. 

The result of this situation is that development of the manager frontend is largely dominated by developers that are comfortable with both ExtJS and PHP code. Server-side handling is limited to actions presented in ExtJS. It’s also not feasible to develop alternative interfaces that do not follow the exact same patterns.

### Decoupling the backend from the frontend 

To decouple the backend PHP code from the frontend manager interface, the interaction with the back-end should be standardized and **resource-oriented** instead of **action-oriented**. 

Transforming the current connector/processor approach into a RESTful API can provide that change. In a RESTful API the resources are central. The resources might be `plugin`, `user`, or `usergroup/members`, and each object can be retrieved or manipulated through GET, POST, PUT and DELETE requests. 

By first defining a specification of the available resources, or endpoints, developers can also build integrations against this specification, even if the API itself is rewritten with different technology in years to come. [Semantic versioning](http://semver.org) of the API specification should be used.

This decoupling will allow backend developers to focus on what they do best, while frontend developers and designers can collaborate to build innovative manager interfaces without also requiring a backend developer. 

### Moving towards a RESTful API

The move towards a RESTful API can be started today, with the current version of MODX, and further integrated into the core in future versions. 

This proposal consists of 4 steps.

1. Define a specification for the API. This includes defining each of the resources (endpoints), its accepted parameters, and return structure/values. The specification may also include details on authentication and other requirements for spec-compliant APIs. 

2. Build the RESTful API. The library or framework to use for this is to be determined, however the API will initially be developed as a standalone Extra, distributed via MODX.com. Add-on developers and site builders can start developing with this RESTful API as a dependency for their projects, and the specification and API can evolve during this process. 

3. To start moving the MODX Manager away from the connectors/processors, an ExtJS wrapper can be developed. This wrapper would cause ExtJS to send requests to the new API in a RESTful fashion, without requiring a complete rewrite to function. 

4. In a breaking release (e.g. 3.0) the RESTful API and the ExtJS wrapper would be incorporated into the core. The no-longer used connectors and processors can then be deprecated or removed from the code. 

### New Manager Interface

This recommendation or the proposed RESTful API does not define what framework or library (if any) should be used in a new manager interface. This is on purpose.
 
As soon as the RESTful API is available (step 2 above), designers and frontend developers can collaborate on a completely rewritten manager interface, that uses the RESTful API instead of the action-oriented connectors/processors. Depending on the results of this collaboration, step 3 may no longer be necessary.

Should the synchronous form-based interaction recommendation be accepted, a server-side wrapper for the API could be developed that handles form-based interactions. 

### Breaking Changes & Other Considerations

The biggest breaking change as a result of this recommendation is the removal of the connectors and processors in step 4. This will affect usage of the $modx->runProcessor() method, which is fairly common in certain types of extras. It may be possible to create a backwards compatible solution where runProcessor is mapped to the new APIs, however by providing the API as an extra before it is incorporated in the core, it is hoped that extra developers start to enhance and update their code before the change is made in the core.

Additionally, any client-side extra that may extend or mimic core manager functionality may be affected by step 3 or 4 of the proposed process. 

Another consideration of providing a full RESTful API is that, with the proper authentication and permissions, it could also be used in frontend (site/user-facing) code. When the WordPress community worked on the WP API initiative, the ability to retrieve information from the site in the front-end was promoted as one of its biggest benefits. This benefit would also be available to MODX following the development of a RESTful API.
