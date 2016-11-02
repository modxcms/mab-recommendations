# Refactor Data Model using xPDO 3.x

_Note: This recommendation is a DRAFT for consideration of the MODX Advisory Board._

The MODX Advisory Board recommends the MODX Project refactor the MODX data model on top of xPDO 3.x to take advantage of autoloading and the removal of map files.

**Editor: Jason Coward**
**First published draft: October 20, 2016**


## Goal of Recommendation

By refactoring the MODX Revolution 3.x data model on xPDO 3.x, MODX can take advantage of proper autoloading, the removal of map files, and other improvements in the 3.x version of xPDO that is now available as a Composer dependency, without introducing a new tool to learn.


## Relevant Recommendations

 * [DRAFT] Refactor MODX Revolution 3.x as Slim 3.x App


## Recommendation

Utilizing xPDO 3.x as the data access layer and O/R mapping library for MODX Revolution 3.x provides a fast track to improve the core model code. Following is a list of benefits of using xPDO 3.x instead of adopting an entirely new O/R mapping tool for the release.

* Avoids a large learning curve for existing contributors already familiar with xPDO.
* Easier to maintain maximum backwards compatibility while modernizing the code.
* Utilizing standard autoloading will help decouple the model from the xPDO library.
* The lack of map files will reduce the overall file count significantly in the MODX core model.
