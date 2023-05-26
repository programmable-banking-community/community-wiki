# 👤 How to authenticate

{% embed url="https://www.loom.com/share/4c0281f1621a4fbb8886547bb38aa4ee" %}

Before you query the Investec API for an account’s history, you must first authenticate. This is how the Investec API safeguards your account.

You must first retrieve a secure access token, formally called a bearer token, to be used in all outbound API calls.

There is a community-contributed [**Postman Collection**](https://www.postman.com/investec-open-api/workspace/programmable-banking/overview) that we recommend you fork as you follow along. The Postman collection includes both the 🏦 Private Banking and 🧰 Corporate Investment Banking (CIB) APIs.

To get a bearer token:

* Send an API request to the https://openapi.investec.com/identity/v2/oauth2/token endpoint.&#x20;
* The endpoint receives your client ID and client secret as [BASIC](https://en.wikipedia.org/wiki/BASIC) authentication headers. Additionally, you must send your API key in an x-api-key header.
* The request body must have a field grant\_type with value client\_credentials.
* It will return a bearer token that you can use in all subsequent API requests. The token is valid for 30 minutes, and you can always request a new one.

The Postman collection comes with an "Authentication -> 200 - OK" request that you can can run with your account credentials to try this out for yourself. 🎉\


You will want to set your credentials as variables in the collection for ease of reuse. The collection comes with client\_id, client\_secret and api\_key variables. You'll find the Variables tab after selecting the Edit menu.

![](<../../.gitbook/assets/image (2).png>)

If your keys are valid, the response will contain the token and an expiration when you send the request.

Here’s an example response:&#x20;

```json
{
  "access token": "qwertyuiop123456789",
  "token_type": "Bearer",
  "expires_in": "1799",
  "scope": "accounts",
 }
```
