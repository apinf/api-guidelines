### Request structure



#### URL Structure

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

The resource is always a noun in plural in the API endpoint and if we want to access one instance of the resource, we pass the id in the URL.

* method `GET path /organizations` gets the list of all Organizations
* method `GET path /organizations/:id` gets the detail of Organization identified with :id
* method `DELETE path /organizations/:id` should deletes Organization identified with :id
* In some cases, if we have resources under a resource, e.g Managers of an Organization, then the sample API endpoints would be:
  * `GET /organizations/:id/managers` should get the list of all Managers from Organization :id
  * `GET /organizations/:id/managers/:managerId` should get the details of Manager :managerId, which belongs to Organization :id
  * `DELETE /organizations/:id/managers/:managerId` should delete Manager :managerId, which belongs to Organization :id
  * `POST /organizations` should create a new Organization and return the details of the new Organization created

The paths should contain the **plural form of resources** and the HTTP method should define the **kind of action** to be performed on the resource. The actual API functionality is implemented under the endpoint.



#### Request parameters

There are three ways to give parameters in request.

* as part of URL
* as query parameters
* in body

##### Parameters as part of URL

In next example there are two parameters provided as part of URL.

`GET /organizations/:id/managers/:managerId`

Parameter :id refers to Organization ID. Parameter :managerId refers to Manager ID.



##### Parameters as query parameters

In next example are queried Users, who's document in database contains string `apinf` in field username  or in field company name or in field email address. In case those are found, for pagination, fifteen first documents are skipped and then next five documents are returned as response.

As a convention the query condition parameter is named as `q`. The convention for naming pagination parameters is to use names `skip` and `limit`.

GET /users?q=apinf&skip=15&limit=5



##### Parameters in body

In case methods POST or PUT is used, the necessary parameters are included in request body as type JSON. Because the parameters usually refer to fields in database, the convention for parameter naming is to use camelCase in order to maintain consistency.













