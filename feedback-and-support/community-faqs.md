---
description: Common questions asked in the community
---

# Community FAQs

We collated a list of some of the most common questions community members are asking. We'll grow this list with your support :clap:

If you have a question that isn't covered by these FAQs, post it on the [Slack channel](https://offerzen-community.slack.com/archives/C048HKU4P0X) 💬

And if you find the solution to an error or a bug, write is down, post in the [Slack channel](https://offerzen-community.slack.com/archives/C048HKU4P0X) or record a quick video. Chances are other developers are having the same issue, and you might save them a lot of time 💜

## 🖥️ Investec API FAQs

<details>

<summary>How do I create a new or multiple Investec API key(s)?</summary>

You can create API keys for your account by logging into the [Investec Online Portal](https://login.secure.investec.com/wpaas/usrroot-wpaas/login/form). Navigate to "Tools" -->  “Programmable Banking” to access your API credentials and create API key(s).&#x20;

Check out [How to Get your API Keys](https://offerzen.gitbook.io/programmable-banking-community-wiki/get-started/api-quick-start-guide/how-to-get-your-api-keys) for more details.

</details>

<details>

<summary>How do I authenticate and obtain an access token to use the Investec Programmable Banking APIs?</summary>

The authentication process involves obtaining an access token using the OAuth 2.0 Authorisation Framework. You'll need to make a request to the authentication endpoint with your client credentials to receive the access token.&#x20;

Check out [How to authenticate](https://offerzen.gitbook.io/programmable-banking-community-wiki/get-started/api-quick-start-guide/how-to-authenticate) for more details.

</details>

<details>

<summary>What are the main API endpoints and methods available for accessing account and transaction information?</summary>

The API provides several endpoints, such as "Get Accounts," "Get Account Balance," and "Get Account Transactions," which allow you to retrieve account details, balances, and transaction information. These endpoints support HTTP methods like GET and POST.

Check out [How to get your transaction history](https://offerzen.gitbook.io/programmable-banking-community-wiki/get-started/api-quick-start-guide/how-to-get-your-transaction-history) for more details.

</details>

<details>

<summary>How do I obtain a list of accounts associated with a profile?</summary>

You can use the "Get Accounts" endpoint (GET /za/pb/v1/accounts) to obtain a list of accounts associated with a profile. This endpoint requires the authorisation bearer token.

Check out [How to get your transaction history](https://offerzen.gitbook.io/programmable-banking-community-wiki/get-started/api-quick-start-guide/how-to-get-your-transaction-history) for more details.

</details>

<details>

<summary>How do I retrieve the balance of a specific account?</summary>

You can use the "Get Account Balance" endpoint (GET /za/pb/v1/accounts/{accountId}/balance) to retrieve the balance of a specific account. Replace {accountId} with the actual account ID.

Check out [How to get your transaction history](https://offerzen.gitbook.io/programmable-banking-community-wiki/get-started/api-quick-start-guide/how-to-get-your-transaction-history) for more details.

</details>

<details>

<summary>How do I fetch transactions for a specific account within a specified date range?</summary>

You can use the "Get Account Transactions" endpoint (GET /za/pb/v1/accounts/{accountId}/transactions) to fetch transactions for a specific account. You can provide optional query parameters such as _fromDate_, _toDate_, and _transactionType_ to filter the transactions.

Check out [How to get your transaction history](https://offerzen.gitbook.io/programmable-banking-community-wiki/get-started/api-quick-start-guide/how-to-get-your-transaction-history) for more details.

</details>

<details>

<summary>How do I list transactions on the API that have not moved to POSTED yet (ie. pending transactions)? </summary>

It is not currently possible to list pending transactions on the API, however, you can calculate pending transactions using the following formula:

\[Available balance] - \[Actual balance] - \[Overdraft limit value] = Pending transactions

</details>

<details>

<summary>Why is the Posted Order of my transactions =0 ? </summary>

The Posted Order of a transaction may start out listed as 0 and then change to the correct number once it has settled. To be safe, ignore transactions while their Posted Order =0.&#x20;

</details>

<details>

<summary>What is the difference between the fields transactionDate and postingDate? </summary>

_transactionDate_ is the date that you swiped your card or issued a payment. _postingDate_ is the date that the amount was deducted from your balance.&#x20;

</details>

<details>

<summary>What are the main API endpoints and methods available for making account transfers and beneficiary payments?</summary>

**Transfer Multiple v2**

* **Endpoint**: ‘POST /za/pb/v1/accounts/{acountId}/transfermultiple’
* **Method**: POST
* **Description**: Allows you to transfer funds to one or multiple accounts.
* **Request body**: The request body should include an array of transfer objects specifying the beneficiary account, amount, and reference details.\


**Pay Multiple:**

* **Endpoint**: ‘POST /za/pb/v1/accounts/{accountId}/paymutiple’
* **Method**: POST
* **Description**: Enables you to pay funds to one or multiple beneficiaries.
* **Request** **Body**: The request body should include an array of payment objectives specifying the beneficiary, amount, and reference details. \


To initiate transfers and payments, make a HTTP POST request to the respective endpoints mentioned above. Ensure that you include the necessary authorisation and authentication headers, and the Bearer token obtained through the OAuth process, to authenticate your API request.&#x20;

\
View the [Investec Developer Docs](https://developer.investec.com/za/api-products) for more details.

</details>

<details>

<summary>Can I create a beneficiary via the API? </summary>

Currently, the API does not support direct creation of beneficiaries. To create a beneficiary, use the[ Investec Online Portal ](https://login.secure.investec.com/wpaas/usrroot-wpaas/login/form)or other standard methods provided by Investec.&#x20;

Once you have created a beneficiary, make at least one payment to that beneficiary using Investec Online before initiating a payment via the API. This ensures that the beneficiary is properly set up and ready to receive payments via the API.

</details>

<details>

<summary>Is there a payment limit on the Beneficiary Payments API?</summary>

The payment limit via the API is currently R20 000.00. You must have made a payment to the beneficiary via [Investec Online](https://login.secure.investec.com/wpaas/usrroot-wpaas/login/form) before making a payment to a beneficiary via the API.

Check out [How to make a payment](https://offerzen.gitbook.io/programmable-banking-community-wiki/get-started/api-quick-start-guide/how-to-make-a-payment) for more details.&#x20;

</details>

## 💳 Card FAQs

<details>

<summary>Where do I access the Online IDE to program my card? </summary>

Login to the [Investec Online Portal ](https://login.secure.investec.com/wpaas/usrroot-wpaas/login/form)and navigate to Programmable Banking. Navigate to the desired card on your profile and ensure that you have enabled it for Programmable Banking by toggling the button below the card. Click on the card to open up the Online IDE.

Check out [How to activate your card for Programmable Banking](https://offerzen.gitbook.io/programmable-banking-community-wiki/get-started/card-quick-start-guide/how-to-activate-your-card-for-programmable-banking) for more details.

</details>

<details>

<summary>How do I intercept and modify card transactions using custom code?</summary>

You can use the beforeTransaction method in the main.js file to intercept the authorization object before it is approved by Investec. Within this method, you can apply logic to either approve or decline the transaction based on the authorization data or external data sources.

Check out H[ow to add code to your card](https://offerzen.gitbook.io/programmable-banking-community-wiki/get-started/card-quick-start-guide/how-to-add-code-to-your-card) for more details.

</details>

<details>

<summary>Can I approve or decline a transaction based on specific conditions?</summary>

Yes, you can apply conditional logic within the beforeTransaction method to approve or decline a transaction based on specific criteria. For example, you can check the transaction amount, beneficiary details, or other factors to determine the appropriate action.

Check out H[ow to add code to your card](https://offerzen.gitbook.io/programmable-banking-community-wiki/get-started/card-quick-start-guide/how-to-add-code-to-your-card) for more details.

</details>

<details>

<summary>How do I perform actions or communicate with external resources after a transaction is completed?</summary>

You can use the afterTransaction method to perform actions or communicate with external resources after processing the transaction. For example, you could set up email notifications every time you swipe your card.

</details>

<details>

<summary>Are there any limitations or time constraints on executing custom code for card transactions?</summary>

The beforeTransaction method has a limited window of 2 seconds to execute, so it's important to ensure your code is efficient and responds within that timeframe. However, the afterTransaction method provides a larger window of 15 seconds for post-transaction actions.

</details>

<details>

<summary>How do I securely manage and reference environment variables for my custom code on the card?</summary>

Environment variables can be defined and saved in the env.json file. These variables can then be accessed within the main.js file using process.env.variableName. This allows you to securely store and reference sensitive information or configuration details.

</details>

<details>

<summary>How do I differentiate between simulated transactions and production transactions?</summary>

You can differentiate between simulated transactions and production transactions by checking the transaction reference. In the afterTransaction method, you can compare transaction.reference with a specific value (e.g., "simulation") to identify simulated transactions.

Check out [How to simulate a transaction](https://offerzen.gitbook.io/programmable-banking-community-wiki/get-started/card-quick-start-guide/how-to-simulate-a-transaction) for more details.

</details>

💡  It's always recommended to consult the [official documentation](https://developer.investec.com/za/api-products) provided by Investec for detailed instructions and specific technical guidance
