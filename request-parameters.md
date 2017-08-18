# Request parameters

There are three ways to give parameters in request.

* as part of URL
* as query parameters
* in body

All parameters, they types and the way they are used must be described in generated documentation.

## Parameters as part of URL

One or several parameters can be provided as part of URL.

* `GET /organizations/:id/managers/:managerId`

  * In example there are provided two parameters. Parameter `:id` refers to Organization ID. Parameter `:managerId` refers to Manager ID. As a response is returned the Manager by managerId in the Organization by :id \(if both are found\).

## Parameters as query parameters

When using GET method, one or more query parameters can be appended in URL.   
The parameters can be used when filtering dataset. As a convention in APInf the query condition parameter is named as `q`.

* `GET /users?q=apinf`
  * In example there are queried Users, who's document in database contains string `apinf` 

It depends on implementation, in which fields in database the actual filtering is performed. In APInf case as a response to the example query are returned Users, who's document in database contains string `apinf` in field username  or in field company name or in field email address.



### Pagination

In case the dataset, and expected response list, is large, the query parameters can be used in pagination. The APInf convention for naming pagination parameters is to use names `skip` and `limit`.

* Parameter **limit **indicates the number of documents to return. 
* Parameter **skip **indicates the number of documents to skip before beginning to return list of documents.

In next example fifteen first found documents are skipped and then next five documents are returned as response.

`GET /users?skip=15&limit=5`



### Date and Time formatting

Dates and times are returned in ISODate format, e.g. 2012-07-14T01:00:00+01:00.

## Parameters in body

In case methods POST or PUT is used, the necessary parameters are included in request body as type JSON. Because the parameters usually refer to fields in database, the APInf convention for parameter naming is to use camelCase in order to maintain consistency.

