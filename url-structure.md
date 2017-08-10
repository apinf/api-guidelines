### URL Structure

The URL is a sentence, where HTTP methods are verbs and resources are nouns.

#### HTTP methods \(verbs\)

* GET method requests data from the resource and should not produce any side effect.

  E.g `/users` returns list of all users

* POST method requests the server to create a resource in the database.

  E.g `/organizations/:id/managers` creates a new Manager of Organization identified with :id.

  * POST is non-idempotent which means multiple requests will have different effects.
    E.g. When requested with same parameters: at first time new Manager is created, at second time an error response \(manager already exists\) is gotten.

* PUT method requests the server to update resource.   
  In our APIs it is not possible to create a resource with PUT method, because resources are referenced with :id. In case resource with :id does not exist, a response with 404 Resource not found is sent.

  E.g. `/organizations/:id` will request the server to update the resource \(identified with :id\) in Organizations collection.

  * PUT is idempotent which means multiple requests will have the same effects.

    E.g. When request with same parameters is sent, the result is same at every time, either successful update or resource not found.

* DELETE method requests that the resources, or its instance, should be removed from the database.  
  E.g `/apis/:id` will request the server to delete the API identified with :id from Apis collection.



#### API Endpoint

The resource is always be plural in the API endpoint and if we want to access one instance of the resource, we pass the id in the URL.

* method `GET path /organizations` gets the list of all Organizations
* method `GET path /organizations/:id` gets the detail of Organization identified with :id
* method `DELETE path /organizations/:id` should deletes Organization identified with :id
* In some cases, if we have resources under a resource, e.g Managers of an Organization, then the sample API endpoints would be:
  * `GET /organizations/:id/managers` should get the list of all Managers from Organization :id
  * `GET /organizations/:id/managers/:managerId` should get the details of Manager :managerId, which belongs to Organization :id
  * `DELETE /organizations/:id/managers/:managerId` should delete Manager :managerId, which belongs to Organization :id
  * \`\`POST /```organizations`` ```should create a new Organization and return the details of the new Organization created



