### Versioning

When APIs are being consumed by the world, upgrading the APIs with some breaking change would also lead to breaking the existing products or services using APIs.

There are mixed opinions around whether API version should be included in the URL or in a header.

In order to ensure browser explorability of the resources across versions, the APInf convention is to have the version in the URL of APIs.

Example:

`https://apinf.io/rest/v1/apis` 

If there is any major breaking update, we can name the new set of APIs as `v2` or `v1.x.x`

