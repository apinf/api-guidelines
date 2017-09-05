# Documentation

## Conventions

There are two alternatives to create APIs: design first and code first. For practical reasons,** we use code first approach**.

The APInf convention in API documentation is following:

* Each \(for User point of view\) API must generate own swagger document about it's functionality.
  * Documentation must contain a general level description about functionality
  * Each endpoint must be documented
  * Description of each request and response message
    * all parameters must be described
      * parameter type
      * parameter location \(path, query, body\)
      * is parameter mandatory or optional
  * Examples of typical use cases.
  * Simple examples of calling API and getting responses.
* Swagger document generation relies on Restivus Swagger plugin \([https://github.com/apinf/restivus-swagger\](https://github.com/apinf/restivus-swagger%29\).
* Documentation is written in Restivus Swagger documentation description fields.
* Note! When writing multiline documentation with markdown, use backticks \(\`\`\) instead of single quotes \(''\) as documentation field separators.
* When adding a functionality in API, the generated documentation must be updated accordingly update

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
  * route for swagger document generation is defined.
* **functionality and swagger metadata file**
  * the actual functionality is implemented 
  * the swagger metadata is defined for **each endpoint** in swagger attribute.

## Current APIs

At the moment the following APIs have been implemented.

**APinf Catalog API** contains API functionality of adding, modifying and deleting.

* swagger object definition
  *  /packages/rest\_apis/catalog.js
* functionality and swagger metadata 
  * /packages/apis/server/api.js
* link to created JSON file for swagger document 
  * &lt;path&gt;/catalog.json

**APInf Management API** contains Organization and Users management functionality.

* swagger object definition

  * /packages/rest\_apis/management.js

* functionality and swagger metadata 

  * for organizations

* /packages/organizations/server/api.js 
  * for users
* /users/collection/server/api.js 
  * link to created JSON file for swagger documen

* &lt;path&gt;/management.json



