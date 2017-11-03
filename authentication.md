# Authentication and API Keys

Authentication is implemented according to functionality in [Restivus Swagger](https://github.com/apinf/restivus-swagger).

1. The user must have a valid user account. 
2. The user logs in via API.
   1. The username and password are given as parameters in login request.
   2. The login credentials \(a **user ID** and a **authentication token**\) are returned in response.
3. When sending requests via API, the user gives the login credentials as parameters in header of request message \(in fields `X-User-Id` and `X-Auth-Token`\). 

Each API documentation must also contain a **login **endpoint. This way the user is able to log in and get user ID and Authentication token, which are needed in order to explore the API functionality with OpenAPI \(formerly Swagger\) specification.

Note! Some of the top level GET methods do not need authentication. However, an API key is needed in those cases. It is conveyed as a header parameter in field`X-Api-Key.`

## Calling API via UI, preparing for a preflight OPTIONS request

When an HTTP request to API is done via a browser, the browser might trigger a CORS preflight request in order to find out, if the original request is allowed. For more details see [https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS.](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

Usually APIs in APInf catalog are connected to a \(API Umbrella\) proxy. Because proxy use requires an API key, examining API functionality using OpenAPI specification UI \(previously called as Swagger\) is one of those cases, which trigger preflight CORS operation.

### Steps

1. Original request is sent, e.g. GET /organizations
   1. request contains header X-Api-Key \(value API key\), which triggers the CORS functionality in browser
2. Browser sends OPTIONS request to proxy \(same address as original request\)
   1. request does not contain header X-Api-Key
   2. request contains header Access-Control-Request-Headers \(value string X-Api-Key\)
3. **Pitfall 1**
   1. because of missing header X-Api-Key, the proxy rejects the OPTIONS request causing original operation to fail
   2. CURE: configure API Umbrella to accept OPTIONS request without header X-Api-Key
4. \(After configuration\) the API Umbrella accepts the OPTIONS request and conveys it to API
5. API receives OPTIONS request and fills supported headers into Access-Control-Allow-Headers for OPTIONS response
6. **Pitfall 2**
   1. Although API does not necessarily use the X-Api-Key header,_ it has to fill the X-Api-Key header_ into A-C-A-H list in response in addition to other headers
7. API sends OPTIONS response to API Umbrella
8. API Umbrella conveys OPTIONS response to the browser
9. The browser compares A-C-R-H list in original GET request to A-C-A-H list in OPTIONS response
10. Browser sends
    1. In case X-Api-Key \(or any of requested headers\) is missing from A-C-A-H, the browser rejects the original request
    2. In case A-C-R-H and A-C-A-H match, browser sends the original request

### Conclusion:

API must contain a handling for OPTIONS request and it must response with support for X-Api-Key header in order to allow API use also via UI.

