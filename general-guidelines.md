# General guidelines

This document provides guidelines and examples for APInf APIs.

Our goal is consistency, maintainability, and best practices across applications. APInf APIs aim to balance a truly RESTful API interface with a positive developer experience \(DX\).

In a nutshell:

* Keep APIs' functionalities as simple as possible. The endpoints do only one thing, but they do it well.
* Avoid overlapping functionalities between different APIs.
* In error case include in the API response verbose description. 
  * include also a description about erroneous parameter value, if it is feasible.
* Implement in each API \(or bundle of APIs\) ability to generate of its own OpenAPI specification about it's functionality.
* API must have support for the OPTIONS endpoint

Minimum developer experience

* Each API in production must be in Catalog, connected in proxy and API key must be used in call.
* Each API must have documentation, preferably OpenAPI specification.
* The description of API must be sufficient.
* Each API must have own logo



