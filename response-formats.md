# Response formats

## Successful responses \(2xx\)

When successful response \(HTTP response codes 2xx\) is returned, the header contains the HTTP response code and the body of response message contains detailed information in human readable format as JSON:

* **title**, describing operation outcome. 
  * E.g. text `Organization added successfully`
* **data**, containing data of one or more entities being object of operation. 
  * E.g. newly added Organization data
  * it is decided case by case, which fields of document\(s\) returned from collection are included in the response message. 

Details of returned data depends on operation.

Esimerkki JSON-koodina vastauksesta...

## Request validation

When handling any request, API must check whether

* User requesting an operation has an account
* the targeted resource exists
* the user is authorized to make the operation in question
* all required parameters provided in request
* request content is valid according to the data model

In case validation fails, operation is stopped and an appropriate error response is sent. In case validation is passed, the request process continues.

Partial updates are not allowed. Consistency between database objects must be maintained... When resources are handled the API functionality must be planned such a way, that in successful case all requested resources are updated and in failure case none of the requested resources are updated.

Keep API purpose and functionality as simple as possible. Do not try to overload API functionality.

## Error handling

Provide a useful error message: the header must contain the HTTP response code and the body of response message must contain detailed information in human readable format as JSON.

API must not return an uncontrolled error response.

> Note! However, the situation when an :id is missing from middle of the URL, is hard to catch.  
> E.g. in case  
> `POST /organizations/:id/managers/:managerId` is erroneously given in form  
> `POST /organizations//managers/:managerId`  
> When the Restivus is trying to analyse the path to endpoint, the missign `:id` causes   the parts in URL path to shift. Instead of `:id` the string 'managers' is tried to be analysed and instead the string 'managers' the `:managerId,` , which causes Restivus to lose the path.

The API returns always sensible HTTP status codes: 

* 400 series status codes for client issues 
* 500 series status codes for server issues. 

Each API standardizes all 400 series errors to come with consumable JSON error representation. If possible \(i.e. if load balancers & reverse proxies can create custom error bodies\), this can be extended to 500 series status codes.

A JSON error body provides a few things for the developer

* a useful error message
* a unique error code \(that can be looked up for more details in the docs\)   _//  &lt;-- TBD  Will we have this?_
* a detailed description. 

JSON output representation looks like this:

```
{
  "code" : 1234,
  "title" : "Organization is not found",
  "detail" : "Organization with specified ID is not found"
}
```

With validation errors for PUT, PATCH and POST requests will need a field breakdown. This can be modeled by using a fixed top-level error code for validation failures and providing the detailed errors in an additional errors field, like so:  _// &lt;-- TBD is this too detailed?_

```
{
  "code" : 1024,
  "title" : "Validation Failed",
  "detail" : [
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

## Documentation of Response formats

Details of returned data must be described in generated documentation.

