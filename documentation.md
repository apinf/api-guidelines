### Documentation

Each \(for User point of view\) API generates own swagger document about it's functionality.

Swagger document generation relies on Restivus Swagger plugin \([https://github.com/apinf/restivus-swagger\](https://github.com/apinf/restivus-swagger%29\).

For APInf developer point of view an API consists of two or more files.

* In **swagger object definition file** the swagger object is defined, attached and a route for swagger is defined.
* In **functionality and swager metadata files** the actual functionality is implemented and the swagger metadata is defined for each endpoint in swagger attribute.

At the moment there are following APIs implemented.

**Catalog API** contains API management functionality.

* swagger object definition: /rest\_apis/catalog.js

* functionality and swagger metadata: /apis/server/api.js

**Management API** contains Organization and Users management functionality.

* swagger object definition: /rest\_apis/management.js

* functionality and swagger metadata for organizations: /organizations/server/api.js

* functionality and swagger metadata for users: /users/collection/server/api.js



