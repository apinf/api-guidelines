# API Design process

In APInf we use unified process for Platform API development. Platform APIs are non-profit APIs. Our intention is not to charge clients for using them. They are part of the platform. 

For each platform API we have two versions: 
- production and 
- design

Production API is the live one and fully functional version. The design has been frozen. It might change, but changes are not backwards breaking. Design version is the next API version (minor/major changes). 


[PIC HERE]

## 1. Define typical use cases

## 2. Design first

### New API

- If this is the first time API is designed, create new open api spec file
- Create API in apinf.io portal and add design to the API. 

### New version of existing API

- In case there is already existing production version API. 
- Create API in apinf.io portal and use lifecycle phase "Design"
- Add open api spec of the production version with modifications needed based on the new use cases. 

## 3. Publish design for broad feedback

- Publish the design in apinf.io portal and post a tweet to Twitter (include handle @apinf_io). 
- Write a blog post about new version development to medium.com/apinf 
- Everytime you find something that needs to be modified, do it and go to next step. 
- Most likely you will go back and forth between this step and next step for afew weeks. 

## 4. Modify design and push back to apinf portal


## 5. Get final review

- Ask feedback from trusted 3rd party API heavy consumers we have contact with. Get atleast 5 persons to do review. 
- Ask feedback to be added to API-portal feedback tab. Accept also direct feedback via other channels. 

## 6. Implement and test
- Take into account last comments from final review
- Do code
- Pull OpenAPI spec from code and store in github. 

## 7. Release

- Link (as URL) generated OpenAPI spec to API in APInf.io catalog. 
- Developers can now see the final API and nice live documentation in APInf.io portal. 
- Once you're done, go back to step 1. 

