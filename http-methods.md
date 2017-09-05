# HTTP methods \(verbs\)

## Used HTTP methods

The APInf APIs use following HTTP methods: GET, POST, PUT and DELETE.

### GET \(read\)

The GET method requests data from the resource and **should not produce any side effect**.  
The possible parameters are sent as part of the URL or as query parameters.

* E.g `GET /users`
  * returns list of all users
* E.g `GET /users?limit=10&skip=30`
  * returns list containing 10 users after skipping 30 users

### POST \(create\)

The POST method requests the server to create a resource in the database.  
The payload is sent in request message body.

POST is a non-idempotent operation which means that multiple requests targeted to same endpoint with same payload will have different outcome.

* E.g `POST /organizations/:id/managers`
  * First attempt creates a new Manager of Organization identified with :id. \(If it did not exist already\).
* E.g `POST /organizations/:id/managers`
  * Second attempt with same payload fails \(because manager already existed\) and an error response \(4xx, manager already exists\) is returned.

### PUT \(update\)

The PUT method requests the server to update a resource. The payload is sent in request message body.

In APinf APIs it is not possible to create a resource with PUT method, because resources are referenced with :id. In case resource with :id does not exist, a response with `404 Resource not found` is sent. Use POST to create a new resource.

PUT is an idempotent operation which means multiple requests with same payload targeted to same endpoint will have the same effect and outcome, either successful update or  resource not found.

* E.g. `PUT /organizations/:id`

  * First attempt will request the server to update the resource \(identified with :id\) in Organizations collection.
    * A successful response with 2xx is returned, if resource is found.
    * In case resource is not found, an error response with 4xx is returned. 

* E.g. `PUT /organizations/:id`

  * Second attempt \(with same payload\) will request the server to update the resource \(identified with :id\) in Organizations collection.
    * A successful response 2xx is returned, if resource is found. 
    * In case resource is not found, an error response with 4xx is returned.

### DELETE \(delete\)

DELETE method requests that the resource, or its instance, should be removed from the database. **Operation is irreversible**.

* E.g `DELETE /apis/:id` 
  * Will request the server to delete the API identified with :id from Apis collection.
    * In a successful case a response with 204 is returned \(no payload included\).
    * In an unsuccessful case a response with 4xx is returned.

## Documentation of used HTTP methods

All used methods and their parameters must be described in generated documentation endpoint by endpoint.

