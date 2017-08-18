# Response formats

## Successful responses

When successful response \(HTTP response codes 2xx\) is returned, the message contains the HTTP response code and the body of response message contains parameters:

* **title**, describing operation outcome. 
  * E.g. text `Organization added successfully`
* **data**, containing data of one or more entities being object of operation. 
  * E.g. newly added Organization data
  * it is decided case by case, which fields of document\(s\) returned from collection are included in the response message. 

Details of returned data depend on operation.

## Error handling

Similarily as an HTML error page shows a useful error message to a visitor, an API provides a useful error message in a known consumable format. The representation of an error should be no different than the representation of any resource, just with its own set of fields.

The API should always return sensible HTTP status codes. API errors typically break down into 2 types: 400 series status codes for client issues & 500 series status codes for server issues. At a minimum, the API should standardize that all 400 series errors come with consumable JSON error representation. If possible \(i.e. if load balancers & reverse proxies can create custom error bodies\), this should extend to 500 series status codes.

A JSON error body should provide a few things for the developer - a useful error message, a unique error code \(that can be looked up for more details in the docs\) and possibly a detailed description. JSON output representation for something like this would look like:

```
{
  "code" : 1234,
  "title" : "Organization is not found",
  "detail" : "Organization with specified ID is not found"
}
```

Validation errors for PUT, PATCH and POST requests will need a field breakdown. This is best modeled by using a fixed top-level error code for validation failures and providing the detailed errors in an additional errors field, like so:

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

Details of returned data must be described in must be described in generated documentation.

