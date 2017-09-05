# Authentication and API Keys

Authentication is implemented according to functionality in [Restivus Swagger](https://github.com/apinf/restivus-swagger).

1. The user must have a valid user account. 
2. The user logs in via API.
   1. The username and password are given as parameters in login request.
   2. In response the login credentials \(a **user ID** and a **authentication token**\) are returned.
3. When sending requests via API, the user gives the login credentials as parameters in header of request message \(in fields **X-User-Id** and **X-Auth-Token**\). 

Each API documentation must also contain a **login **endpoint. This way the user is able to log in and get user ID and Authentication token, which are needed in order to explore the API functionality with Swagger document.

Note! Some of the top level GET methods do not need authentication. However, an API key is needed in those cases. It is conveyed as a header parameter `X-Api-Key.`

