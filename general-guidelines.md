### General guidelines

This document provides guidelines and examples for APInf APIs, encouraging consistency, maintainability, and best practices across applications. APInf APIs aim to balance a truly RESTful API interface with a positive developer experience \(DX\).

In a nutshell:

* Keep    APIs' functionalities is kept as simple as possible. The endpoints do only one thing, but they do it well.
* Avoid    No overlapping functionalities between different APIs ~~should ~~be implemented.
*    In error case the API response contains verbose description, 
*   description about erroneous parameter value is included in.
* Each API \(or bundle of APIs\) generate own swagger document about it's functionality.

* _simpler_



