# API Endpoint

The resource is always a noun in plural form in the API endpoint. If we want to access one specific instance of the resource, we pass the id in the URL.

* `GET path /organizations` 
  * gets the list of all Organizations
* `GET path /organizations/:id` 
  * gets the detail of Organization identified with :id
* `DELETE path /organizations/:id` 
  * deletes Organization identified with :id
* If we have resources under a resource, e.g Managers of an Organization, the sample API endpoints would be:
  * `GET /organizations/:id/managers` should get the list of all Managers from Organization :id
  * `GET /organizations/:id/managers/:managerId` should get the details of Manager :managerId, which belongs to Organization :id
  * `DELETE /organizations/:id/managers/:managerId` should delete Manager :managerId, which belongs to Organization :id
  * `POST /organizations` should create a new Organization and return the details of the new Organization created

The paths must contain the **plural form of resources** and the HTTP method must define the **operation** to be performed on the resource. The actual API functionality is implemented under the endpoint in functionality and swagger metadata files.

## Documentation of API Endpoint

Functionality of every endpoint must be described in generated documentation.

