### API Endpoint

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
