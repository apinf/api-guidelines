# Introduction

The APInf REST APIs are the interface, through which developers interact with the data. Our goal is to implement good designed APIs that are always very easy to use and thus make the developers' life very smooth.

> API is the GUI for developers, but if it is confusing or not verbose, then the developer will start finding alternatives or stop using it.  
> -- Mahesh Haldar

We consider the developers’ experience to be the most important metric to measure the quality of the our APIs.

## Terminology

In this guide the following terms are used related to REST APIs

* **Resource** is an object or representation of something, which has some associated data with it and there can be set of methods to operate on it.
  * E.g. apis, organizations and users are **resources**
* **Operation** is a method or set of methods to operate resources
  * list, delete, add, update are the **operations** to be performed on resources
* **URL** \(Uniform **Resource** Locator\) is a path through which a **resource** can be located and some actions can be performed on it.
* **Collection** is a set of resources.


## APInf Platform APIs

Currently we have three (3) APIs in APInf platform. The design of those is inline with the Design Guide and development is done according to the same API Design Guide (this on you are reading). 

* Catalog REST API ([production version](https://apinf.io/apis/apinf-catalog-rest-api-1), [next version design](https://apinf.io/apis/apinf-catalog-rest-api-design))
* Management REST API ([production version](https://apinf.io/apis/apinf-management-rest-api), next version design)
* Analytics REST API ([beta design version](https://apinf.io/apis/apinf-analytics-api))

### Catalog REST API

APInf Catalog REST API enables API management via a simple API. With this API you can list, add, update and remove (CRUD) the APIs in catalog. 

### Management REST API

APInf Management REST API enables Organization and User management via simple API. With this API you can add, list, update and remove (CRUD) catalog content, such as users of the service and information regarding API owner organizations. 

### Analytics REST API

With APInf Analytics REST API you can retrieve general and detailed information about performance of your APIs. With this API you can for example to monitor your API performance or to export API performance data for external dashboard.
