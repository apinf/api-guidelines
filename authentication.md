# Authentication

Authentication is implemented according to functionality in [Restivus Swagger](https://github.com/apinf/restivus-swagger).

Include in each API documentation also login endpoint. This way user is able to log in and explore the API functionality with Swagger document.

_TBD:_

_Originally Jarkko says: _

* _We require API key in all GET methods. You can get it by creating account to Apinf system. Create it now from _[_https://apinf.io/sign-up_](https://apinf.io/sign-up)

_At the moment user can log in and get tokens: userId and auth-token.  _

In endpoints, which do not need authentication - GET methods on top level - an API key is needed.

