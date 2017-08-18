# Documentation

## Conventions

The APInf convention in API documentation is following:

* Each \(for User point of view\) API generates own swagger document about it's functionality.
* Swagger document generation relies on Restivus Swagger plugin \([https://github.com/apinf/restivus-swagger\](https://github.com/apinf/restivus-swagger%29\).
* Documentation is written in Restivus Swagger documentation description fields.
* Note! When writing multiline documentation with markdown, use backticks \(\`\`\) instead of single quotes \(''\) as documentation field separators.

## Files

For developer point of view the APInf APIs consist of two or more files.

* **swagger object definition file** 
  * the swagger object is defined and exposed for use of functionality 
    * meta
      * swagger version
      * info
      * paths
      * security definitions
    * tags
    * params
    * definition
    * 
  * route for swagger document generation is defined.
* In **functionality and swagger metadata files**
  * the actual functionality is implemented 
  * the swagger metadata is defined for **each endpoint** in swagger attribute.

## Current APIs

At the moment there are following APIs implemented.

**Catalog API** contains API management functionality.

* swagger object definition 

  * /packages/rest\_apis/catalog.js

* functionality and swagger metadata 

  * /packages/apis/server/api.js

* link to created JSON file for swagger document

  * &lt;path&gt;/catalog.json

**Management API** contains Organization and Users management functionality.

* swagger object definition

  * /packages/rest\_apis/management.js

* functionality and swagger metadata

  * for organizations

    * /packages/organizations/server/api.js

  * for users

    * /users/collection/server/api.js

* link to created JSON file for swagger documen

  * &lt;path&gt;/management.json



