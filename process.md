# API Design process

In APInf we use unified process for Platform API development. Platform APIs are non-profit APIs. Our intention is not to charge clients for using them. They are part of the platform.

For each platform API we have two versions:

* production and 
* design

Production API is the live one and fully functional version. The design has been frozen. It might change, but changes are not backwards breaking. Design version is the next API version \(minor/major changes\).

![API development process](https://raw.githubusercontent.com/apinf/api-guidelines/master/apinf-api-process.png)

## 0. Define typical use cases

## 1. Design first

### New API

* If this is the first time API is designed, create new open api spec file
* Create API in apinf.io portal and add design to the API. 

### New version of existing API

* In case there is already existing production version API. 
* Create API in apinf.io portal and use lifecycle phase "Design"
* Add open api spec of the production version with modifications needed based on the new use cases. 

## 2. Copy spec to apinf.io

* Publish the design in apinf.io portal and post a tweet to Twitter \(include handle @apinf\_io\). 
* ...

## 3. Get broad feedback 

* Write a blog post about new version development to medium.com/apinf 
* Everytime you find something that needs to be modified, do it and go to next step. 
* Most likely you will go back and forth between this step and next step for afew weeks. 

## 4. Finalize beta

* ...

## 5. Get final review

* Ask feedback from trusted 3rd party API heavy consumers we have contact with. Get at least 5 persons to do review. 
* Ask feedback to be added to API-portal feedback tab. Accept also direct feedback via other channels. 

## 6. Apply changes in design

## 7. Create tests, implement and test

* Take into account last comments from final review
* Define test, implement code. Note! Use automated testing!  
* Build OpenAPI specification in Github \(this is linked to APInf.io API at hand\). 
* Link \(as URL\) generated OpenAPI specification to API in APInf.io catalog. 

## 8. Start again from 0.



