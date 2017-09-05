# Authentication and API Keys

Authentication is implemented according to functionality in [Restivus Swagger](https://github.com/apinf/restivus-swagger).

Avattuna tähän lisää tietoa...

Koodiesimerkkikin käy...

Include in each API documentation also login endpoint. This way user is able to log in and get user ID and Authentication token, which are needed in order to explore the API functionality with Swagger document.

Some of the top level GET methods do not need authentication. However, an API key is needed in those cases. It is conveyed as a header parameter `X-Api-Key.`

