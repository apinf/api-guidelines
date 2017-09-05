# Versioning

When APIs are upgraded with some breaking change, it may lead to breaking existing products or services using upgraded APIs.

Breaking changes are for example ...

In case of breaking changes making a new version of the updated API is mandatory.

There are mixed opinions around about the way the versioning is indicated: whether API version should be included in the URL or in a header.

**The APInf convention is to have the version in the URL of APIs**. The reason is to ensure browser explorability of the resources across versions.

Example:

`https://apinf.io/rest/v1/apis`

If there is any major breaking update, the new set of APIs is named as `v2` .

