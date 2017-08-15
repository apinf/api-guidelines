### Response codes

When the client raises a request to the server through an API, the client should know the feedback, whether it failed, passed or the request was wrong. HTTP status codes are bunch of standardized codes which has various explanations in various scenarios. The server should always return the right status code.

The following are the important categorization of HTTP codes:

#### 2xx \(Success category\)

These status codes represent that the requested action was received and successfully processed by the server.

**200 Ok** The standard HTTP response representing success for GET, PUT and POST.

**201 Created** This status code should be returned whenever the new instance is created. E.g on creating a new instance, using POST method, should always return 201 status code.

**204 No Content** represents the request is successfully processed, but has not returned any content.

DELETE can be a good example of this.

The API `DELETE /organizations/:id/managers/:managerId` will delete the manager `:managerId` and in return we do not need any data in the response body of the API, as we explicitly asked the system to delete. If there is any error, like if manager `:managerId`does not exist in the database, then the response code would be not be of 2xx Success Category but around 4xx Client Error category.

### 3xx \(Redirection Category\)

**304 Not Modified** indicates that the client has the response already in its cache. And hence there is no need to transfer the same data again.

#### 4xx \(Client Error Category\)

These status codes represent that the client has raised a faulty request.

**400 Bad Request** indicates that the request by the client was not processed, as the server could not understand what the client is asking for.

**401 Unauthorized** indicates that the client is not allowed to access resources, and should re-request with the required credentials.

**403 Forbidden** indicates that the request is valid and the client is authenticated, but the client is not allowed access the page or resource for any reason. E.g sometimes the authorized client is not allowed to access the directory on the server.

**404 Not Found** indicates that the requested resource is not available now.

**410 Gone** indicates that the requested resource is no longer available which has been intentionally moved.

#### 5xx \(Server Error Category\)

**500 Internal Server Error** indicates that the request is valid, but the server is totally confused and the server is asked to serve some unexpected condition.

**503 Service Unavailable** indicates that the server is down or unavailable to receive and process the request. Mostly if the server is undergoing maintenance.

