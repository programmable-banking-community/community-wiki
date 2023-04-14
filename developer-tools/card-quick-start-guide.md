# Card Quick Start Guide

:credit\_card: Investec Programmable Cards give you the ability to write custom code for your card, enabling you to to build your own rules and limits that execute before and after your card transactions.&#x20;

This Quick Start Guide provides a step-by-step for getting started and adding code to your Investec card(s). Learn how to:

* Activate your card for Programmable Banking
* Add code to your code on the Online IDE
* Simulate a transaction on the Online IDE
* Use Programmable Cards via the Card API

{% hint style="info" %}
**Pro-Tip:** Programmable cards use code written in **JavaScript**.
{% endhint %}

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f64c">🙌</span> How to activate your card for Programmable Banking</summary>

* Navigate to [Investec Online Banking](https://login.secure.investec.com/wpaas/usrroot-wpaas/login/form) and login with your details.
* Once you have logged in, you will be presented with your profile. Scroll down to the Programmable Banking section and click ‘Find Out More’

![](<../.gitbook/assets/image (2).png>)

* Navigate to the desired card on your profile and ensure that you have enabled it for Programmable Banking by toggling the button below the card.

![](https://lh5.googleusercontent.com/DZV1p3R\_Dj9Hl2gtX7\_lz6mIjMMglj6AEHro7uuuOXi5wHZuLMQj49v8XdoRofGkLWVcU6Uem-e8TlpHkjbnZZiDg9R-jS4JYRV4Reh5Fny-LQdov6n\_-uVJ\_lBgVMnB\_v-Iccy\_TTdyJ8RROMgNiDw)

**ProTip:** You can enable and disable the code on each card using the toggle below the cards. You can access this via the mobile app if you need to do so while at the shop till.

</details>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f5a5">🖥</span> How to add code to your card on the Online IDE</summary>

There are three main functions that can be used to execute custom functionality on your card:

* **beforeTransaction** - Every time you initiate a transaction from your Investec card, the beforeTransaction method intercepts the authorization object before it is approved by Investec. This gives you the ability to apply logic to either decline or approve the transaction based on data from the card authorization itself. This function needs to return a true or false value in order for it to work. Time is limited for this function so use minimal code.

<!---->

* **afterTransaction** - This function will execute after every transaction that has been processed by the card and it runs after the `before_transaction` function.&#x20;

<!---->

* **afterDecline** - This function will execute if a transaction has been declined on the card.

Once you have enabled your card for Programmable Banking, select the desired card by clicking on the image of the card and you will be presented with the following online editor.

![](https://lh4.googleusercontent.com/wII4bQlHtKCDVkHrZQ1bPP2ReIkGNeISpTbixeaGTghp9Uxc04fEtOa1bgi5IKE5kR\_Elytz6TtDomNfkZ3EoKmYoybrzANFjfWvBJsXdIg6EuWkV0zgLTfxPQu\_P\_9S1qPJZDyMv7zS-ytQk8RuUOY)

**Pro-Tip:** The IDE can be slow to load and you might need to refresh the page.

The file which you will be working on the most is the `main.js` file that is open in the screenshot above. To test out adding code to your card, you can paste the following code snippet into the `main.js` file as shown below. The code snippet declines card purchases that are made in bakeries (using a specified merchant code) and that are over R50 (or 5000 cents). You can add the code snippet to the `main.js` file and it won’t have any effect on your card until you click “deploy code to card”.

**Pro-Tip:** When referring to amounts in the code it is the cent value of the transaction. R55 equals 5050 cents.

````javascript
// ```javascript
const beforeTransaction = async (authorization) => {
  if (authorization.merchant.category.key === 'bakeries') {
    return authorization.centsAmount < 5000
  }
  return true
}
```
````

</details>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4b0">💰</span>How to simulate a transaction on the Online IDE</summary>

On the right hand side of the code editor you will see the simulator. This allows you to simulate transactions to test out the code on your card before you deploy it. Once you have simulated a transaction, you will be presented with the `simulation.json` file which will explain what has happened in the transaction.

![](https://lh6.googleusercontent.com/jemxlBNuf6XqYXnwjc0nsD29ZY-SFqF3awv0437f345YRcxongar6Db3Z-Ozhx00KvlA32aNS7OeRoENg8aomnunucInLzvbIqhzwQt2FMJmXmm0Wg\_doIfb9o9YUN-uAMhCjnxgWrm2Lb5FQOLHcpw)

In the above simulation you can see that the simulated transaction has failed because the amount of R55 (5050 cents) was over the limit specified in the code snippet.

Once you are happy with your code and have tested it out, you may deploy your changes to your card using the “Deploy code to card” button.

**Pro-Tip:** The `log.json` file shows all the logs from the code. You can also log certain outcomes using the `console.log` function.

</details>

:credit\_card: **How to use Programmable Cards via the Card API**

There is a community-contributed[ **Postman Collection**](https://www.postman.com/investec-open-api/workspace/programmable-banking/overview) that we recommend you fork as you follow along in the guide.

In order to use the API, please refer to the [**following guide**](https://offerzen.gitbook.io/programmable-banking-community-wiki/developer-tools/api-quick-start-guide) to get your API Keys and to familiarise yourself with the Authentication process.

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

Congratulations on completing the quick start for Programmable Cards! Once you have completed the guide please feel free to post some details about your code on the [Slack community](https://offerzen-community.slack.com/archives/C04KFQA3YCQ).
