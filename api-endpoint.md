# API Endpoint

The resource is always **a noun in plural form** in the API endpoint. If we want to access one specific instance of the resource, we pass the id of the resource in the URL.

* `GET /organizations` 
  * gets the list of all Organization instances
* `GET /organizations/:id` 
  * gets the details of an Organization instance identified with :id
* `DELETE /organizations/:id` 
  * deletes Organization instance identified with :id
* `POST /organizations` 
  * creates a new Organization and returns the details of the new Organization created

If we have resources under a resource, e.g Managers of an Organization, the sample API endpoints would be:

* `GET /organizations/:id/managers` 
  * returns the list of all Managers from Organization `:id`
* `GET /organizations/:id/managers/:managerId` 
  * returns the details of Manager identified with `:managerId`, which belongs to Organization identified with `:id`
* `DELETE /organizations/:id/managers/:managerId` 
  * deletes Manager identified with `:managerId`, which belongs to Organization identified with `:id`

The paths must contain the **plural form of resources** and the HTTP method must define the **operation** to be performed on the resource. The actual API functionality is implemented under the endpoint in functionality and OpenAPI metadata files.

## Documentation of API Endpoint

Functionality of every endpoint must be described in generated documentation.

