# 💳 How to use the Cards API

There is a community-contributed[ **Postman Collection**](https://www.postman.com/investec-open-api/workspace/programmable-banking/overview) that we recommend you fork as you follow along in the guide.

In order to use the API, please refer to the [following guide](../api-quick-start-guide/how-to-get-your-api-keys.md) to get your API Keys and to familiarise yourself with the Authentication process.

After you have authenticated your API access in Postman, use the following card endpoints:

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4b3">💳</span> Get Cards</summary>

The first step is to call the `GetCards` endpoint. This endpoint returns all the cards associated with a user's account.&#x20;

**ProTip:** When deploying custom code to a given card, you will need to use the `cardkey` variable that is returned from the Get Cards response.

**Example Response**

```json
{
   "data": {
       "cards": [
           {
               "CardKey": "1234567",
               "CardNumber": "123456XXXXXX1234",
               "IsProgrammable": true,
               "Status": "Active",
               "CardTypeCode": "VBC",
               "AccountNumber": "11111111111",
               "AccountId": "1111111111222222222233333",
               "EmbossedName": "T TEST"
           },
       ]
   },
   "links": {
       "self": null
   },
   "meta": {
       "totalPages": 1
   }
}
```

</details>

<details>

<summary>↪️ Update Function Code</summary>

To update the code on your card, we use the `UpdateFunctionCode` endpoint which saves the code to your card (it doesn’t publish it). Replace the `cardkey` attribute in the URL on this endpoint with the `cardkey` variable from the `GetCards` endpoint of the card that you would like the code to be on.

![](https://lh4.googleusercontent.com/bsPNyNw5xAZkmiVafHkVGGm-knX8qH2VJ6dO2FHiSL8rUXhtBZwRMGwfMDZ5wTeHgzwkyI89sUFVynC9pQSs1-bW9F-sdW80kTDc1mmGqu\_k9x8N3L7c1dSfu39S5T-Le4NX0ovAAjRw0EqkZK4W7Po)

Replace the body of the request with the following:

{% code overflow="wrap" %}
````json
```
{
    "code": "const beforeTransaction = async (authorization) => { if (authorization.merchant.category.key === 'bakeries') { return authorization.centsAmount < 5000 } return true}"
}
```
````
{% endcode %}

The above snippet declines a card purchases that are made in bakeries (using a specified merchant code) transactions and that are over the R50 (or 5000 cents) limit

Once you are satisfied with the code, click the send button to update the code onto your card. When your response is successful you should receive the following:

```json
{
   "data": {
       "result": {
           "codeId": "d11bd10e-7cba-1f11-a111-c11e11a1e111",
           "code": "const beforeTransaction = async (authorization) => { if (authorization.merchant.category.key === 'bakeries') { return authorization.centsAmount < 5000 } return true}",
           "createdAt": "2023-04-05T09:33:11.925Z",
           "updatedAt": "2023-04-05T09:33:11.925Z",
           "publishedAt": "2023-04-05T09:33:11.925Z",
           "error": null
       }
   },
   "links": {
       "self": null
   },
   "meta": {
       "totalPages": 1
   }
}
```

The `codeid` returned from the response is uniquely generated every time you post code to your card, which you will need for your next API call.

**Pro-Tip:** this endpoint does not actually publish the code, we will do this in the next step.

</details>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f468-1f4bb">👨💻</span> Publish Saved Code</summary>

The `PublishSavedCod`endpoint will publish the code to the specified card and activate it.&#x20;

We first replace the `cardkey` variable in the URL for the card that you want to publish the code to and replace the body of the request with the following:

```json
{
   "codeid": "d11bd10e-7cba-1f11-a111-c11e11a1e111",
   "code": ""
}
```

**Example Response**

```json
{
    "data": {
        "result": {
            "codeId": "d11bd10e-7cba-1f11-a111-c11e11a1e111",
            "code": "const beforeTransaction = async (authorization) => { if (authorization.merchant.category.key === 'bakeries') { return authorization.centsAmount < 5000 } return true}",
            "createdAt": "2023-04-05T12:36:43.209Z",
            "updatedAt": "2023-04-05T12:36:43.209Z",
            "publishedAt": "2023-04-05T12:36:56.272Z",
            "error": null
        }
    },
    "links": {
        "self": null
    },
    "meta": {
        "totalPages": 1
    }
}
```

**Pro-Tip:** The above response will match the code and `codeid` sent to the card.

</details>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f911">🤑</span> Simulate a transaction</summary>

You will use the `ExecuteFunctionCode` endpoint for testing your code before publishing it onto the card itself. Replace the `cardkey` variable in the URL with the correct `cardkey` you would like to simulate the transaction on. Then replace the body with the following:

```json
{
    "simulationcode": "const beforeTransaction = async (authorization) => { if (authorization.merchant.category.key === 'bakeries') { return authorization.centsAmount < 5000 } return true }",
    "centsAmount": "5050",
    "currencyCode": "zar",
    "merchantCode": 5462,
    "merchantName": "The Coders Bakery",
    "merchantCity": "Cape Town",
    "countryCode": "ZA"
}
```

The above snippet simulates and declines a card purchases that are made in bakeries (using a specified merchant code) transactions and that are over the R50 (or 5000 cents) limit.

![](https://lh4.googleusercontent.com/Npq2CiY9\_IcoOga\_B0Qx4k-LF-5PvGcarJc0glvphtFxNsmuZ7Wx3Iba9qrgqAit1ND1XK7W1P8bi1XKzFZByS95wdGtz5qNB1YD5W\_HO0mH7R8vGsnRHI8izAtrlhaDEFusDX1TJC4PREGKm7gSbuA)

As you can see by the response, the code fails the simulated transaction

</details>
