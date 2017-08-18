# HTTP methods \(verbs\)

* GET method requests data from the resource and should not produce any side effect.  
  The possible parameters are sent as part of the URL or as query parameters.

  * E.g `GET /users`
    * returns list of all users

* POST method requests the server to create a resource in the database.  
  The possible parameters are sent in request message body.  
  POST is a non-idempotent which means that multiple requests will have different effects.

  * E.g `POST /organizations/:id/managers`
    * First attempt creates a new Manager of Organization identified with :id. \(If it did not exist already\).
  * E.g `POST /organizations/:id/managers`
    * Second attempt fails \(because manager already existed\) and an error response \(4xx, manager already exists\) is sent.

* PUT method requests the server to update a resource.  
  The possible parameters are sent in request message body.  
  In our APIs it is not possible to create a resource with PUT method, because resources are referenced with :id. In case resource with :id does not exist, a response with `404 Resource not found` is sent.  
  PUT is idempotent which means multiple requests will have the same effects and outcome, either successful update or  resource not found.

  * E.g. `PUT /organizations/:id`

    * First attempt will request the server to update the resource \(identified with :id\) in Organizations collection. A successful response \(2xx is returned, if resource is found\).

  * E.g. `PUT /organizations/:id`

    * Second attempt will request the server to update the resource \(identified with :id\) in Organizations collection. A successful response \(2xx is returned, if resource is found\).

* DELETE method requests that the resources, or its instance, should be removed from the database. 
  * E.g `DELETE /apis/:id` 
    * will request the server to delete the API identified with :id from Apis collection.



