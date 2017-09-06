# Response formats

## Successful responses \(2xx\)

When successful response \(HTTP response codes 2xx\) is returned, the header contains the HTTP response code and the body of response message contains detailed information in human readable format as JSON:

* **status**, describing operation outcome. 
  * E.g. text `success`
* **data**, containing data of one or more entities being object of operation. 
  * E.g. newly added Organization data
  * it is decided case by case, which fields of document\(s\) returned from collection are included in the response message. 

Details of returned data depends on operation.

Example: response to `GET /organizations/:id`

```
     {
       "_id": "2LSbYwcixbohmwo8Z",
       "name": "APInf",
       "url": "https://apinf.com",
       "description": "Open source API management and catalog",
       "slug": "apinf",
       "managerIds": [
           "peJXS5THJtMssTopq"
       ],
       "createdBy": "peJXS5THJtMssTopq",
       "createdAt": "2017-03-16T19:07:54.575Z",
       "friendlySlugs": {
           "slug": {
               "base": "apinf",
               "index": 0
           }
       },
       "organizationLogoFileId": "c097697707d71196f2f1ec52",
       "updatedAt": "2017-07-19T09:23:51.570Z",
       "featuredApiIds": []
     },
```

## Request validation

When handling any request, API must check whether

* User requesting an operation has an account
* the targeted resource exists
* the user is authorized to make the operation in question
* all required parameters provided in request
* request content is valid according to the data model

In case validation fails, operation is stopped and an appropriate error response is sent. In case validation is passed, the request process continues.

Partial updates are not allowed. Consistency between database objects must be maintained:

* in successful case all requested resources are updated 
* in failure case none of the requested resources is updated.

Keep API purpose and functionality as simple as possible. Do not try to overload API functionality.

## Unsuccessful responses \(3xx/4xx/5xx\)

Provide a useful error message:

* the header must contain the HTTP response code 
* the body of response message must contain detailed information in human readable format as JSON.
  * **status**, describing operation outcome. 
    * E.g. text `fail`
  * **message**, containing description of failure reason
    * E.g. text `Description length must not exceed 1000 characters`

API must not return an uncontrolled error response, but the API returns always a sensible response with HTTP status codes:

* 400 series status codes for client issues 
* 500 series status codes for server issues. 

Each API standardizes all 400 series errors to come with consumable JSON error representation. If possible \(i.e. if load balancers & reverse proxies can create custom error bodies\), this can be extended to 500 series status codes.

A JSON error body provides a few things for the developer

* a useful error message
* a detailed description
* \(to be decided case by case\) a unique error code, which can be looked up for more details in the docs

JSON output representation looks like this:

```
{
  "status" : "fail",
  "message" : "Organization with specified ID is not found"
}
```

\(to be decided case by case\) With validation errors for PUT, PATCH and POST requests will need a field breakdown. This can be modeled by using a fixed top-level error code for validation failures and providing the detailed errors in an additional errors field, like so:  _// &lt;-- TBD is this too detailed?_

```
{
  "code" : 1024,
  "status" : "fail",
  "message" : [
    {
      "code" : 5432,
      "title" : "first_name",
      "detail" : "First name cannot have fancy characters"
    },
    {
       "code" : 5622,
       "title" : "password",
       "detail" : "Password cannot be blank"}
  ]
}
```

> Note! However, the situation when an :id is missing from middle of the URL, is hard to catch.  
> E.g. in case  
> `POST /organizations/:id/managers/:managerId` is erroneously provided in form  
> `POST /organizations//managers/:managerId`  
> When the Restivus is trying to analyse the path to endpoint, the missign `:id` causes   the parts in URL path to shift. Instead of `:id` the string 'managers' is tried to be analysed and instead the string 'managers' the `:managerId,` , which causes Restivus to lose the path.

## Documentation of Response formats

Details of returned data must be described in generated documentation.

