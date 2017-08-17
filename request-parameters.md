# Request parameters

There are three ways to give parameters in request.

* as part of URL
* as query parameters
* in body

## Parameters as part of URL

In next example there are two parameters provided as part of URL.

`GET /organizations/:id/managers/:managerId`

Parameter `:id` refers to Organization ID. Parameter `:managerId` refers to Manager ID. As a response \(if found\) is returned the  Manager by managerId in the Organization by :id.

## Parameters as query parameters

Query parameters can be appended in GET method.

The parameters can be used when filtering dataset. As a convention the query condition parameter is named as `q`.

It depends on implementation, in which fields in database the actual filtering is performed.

In next example are queried Users, who's document in database contains string `apinf` in field username  or in field company name or in field email address.

`GET /users?q=apinf`

### Pagination

In case the dataset is large, the query parameters can be used in pagination. The APInf convention for naming pagination parameters is to use names `skip` and `limit`.

* Parameter **limit **indicates the number of documents to return. 
* Parameter **skip **indicates the number of documents to skip before beginning to return documents.

In next example fifteen first documents are skipped and then next five documents are returned as response.

`GET /users?skip=15&limit=5`

### Date and Time formatting

Dates and times are returned in ISODate format, e.g. 2012-07-14T01:00:00+01:00.

## Parameters in body

In case methods POST or PUT is used, the necessary parameters are included in request body as type JSON. Because the parameters usually refer to fields in database, the APInf convention for parameter naming is to use camelCase in order to maintain consistency.

