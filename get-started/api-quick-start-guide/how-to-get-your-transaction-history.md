# 🏦 How to get your transaction history

The Investec API enables you to query several details about an account. First, we’ll explore how to retrieve an account’s transaction history.

The API endpoint returns a list of transactions between two dates, as specified in your request.

Every account on your bank account has a unique ID that you use when transacting against it. So first, you must obtain the appropriate ID. Fortunately, the Investec API has an easy-to-use endpoint for this.

Using the community-contributed [**Postman Collection**](https://www.postman.com/investec-open-api/workspace/programmable-banking/overview)**,** make an API call to to your Private Bank account using **https://openapi.investec.com/za/pb/v1/accounts**. It does not take any special parameters and returns a JSON list of all your accounts and their IDs.

{% hint style="info" %}
🧰 If you have a CIB account use the following URL instead: **https://openapi.investec.com/za/bb/v1/accounts**
{% endhint %}

Run the Get Accounts request in the Postman collection, and remember to add the bearer token obtained earlier on as variable in your Postman environment.

Below is an example response . You want the value in the “accountId” field.

```json
{
  "data": {
    "accounts": [
      {
        "accountId": "1234567890",
        "accountNumber": "11223344556677",
        "accountName": "Jane Smith",
        "referenceName": "Jane Smith",
        "productName": "Private Bank Account",
        "kycCompliant": true,
        "profileId": "9876543210"
      },
    ]
  },
  "links": {
    "self": "https://openapi.investec.com/za/pb/v1/accounts"
  },
  "meta": {
    "totalPages": 1
  }
}
```

A typical request to retrieve transactions will take the form:

http://api.investec.com/za/pb/v1/accounts/{accountId}/transactions?fromDate={fromDate}\&toDate={toDate}\&page=1.

Where {accountId} is the account ID you have just obtained, whereas fromDate and toDate can be any [ISO 8601](https://en.wikipedia.org/wiki/ISO\_8601) formatted date \[Example of formatted date: 1999-09-09]].

Let’s get transactions from the last month. Our request would be: http://api.investec.com/za/pb/v1/accounts/1234-5678/transactions?fromDate=2023-02-22\&toDate=2023-01-22\&page=1.

You can add these parameters to the _Get Account Transactions_ Postman request, taking care to use the correct account ID.

{% hint style="info" %}
**Pro Tip:** As you may have noticed, the endpoint accepts a pagination parameter for when you need to iterate through a longer transaction history.
{% endhint %}

If you have added the correct account ID, you will get a response with structure:

```json
{
  "data": {
    "transactions": [
      {
        "accountId": "1234567890",
        "type": "DEBIT",
        "transactionType": "OnlineBankingPayments",
        "status": "POSTED",
        "description": "LOREM IPSUM",
        "cardNumber": "",
        "postedOrder": 123,
        "postingDate": "2023-01-10",
        "valueDate": "2023-01-11",
        "actionDate": "2023-01-12",
        "transactionDate": "2023-01-10",
        "amount": 100,
        "runningBalance": 9999.99
      }
    ]
  },
  "links": {
    "self": "https://openapi.investec.com/za/pb/v1/accounts/1234567890/transactions?fromDate=2023-01-01&toDate=2023-01-31"
  },
  "meta": {
    "totalPages": 1
  }
}
```

🧰 An example CIB API response will look like this:&#x20;

```json
{
    "data": {
        "accounts": [
            {
                "AccountHolderAddress": {
                    "AddressLine1": "",
                    "AddressLine2": "",
                    "City": "",
                    "Country": "",
                    "CountryCode": ""
                },
                "RoutingBIC": "",
                "BankAccountProductType": "",
                "CreditLastCycleToNextBusinessDate": "0001-01-01T00:00:00",
                "CustomerAccountType": "",
                "DebitLastCycleToNextBusinessDate": "0001-01-01T00:00:00",
                "DueDateOfPayment": "2023-05-14T22:00:01Z",
                "MinimumAmountLimit": 0,
                "NumberOfCardHolders": 0,
                "CreditLimit": 1,
                "DebitAccountBankName": "",
                "PendingTransactions": 0,
                "Banks": {
                    "Name": "Investec South Africa",
                    "ChipsUID": "",
                    "Branch": [
                        {
                            "Number": ""
                        }
                    ],
                    "PostalAddress": {
                        "AddressLine1": "",
                        "AddressLine2": "",
                        "City": "",
                        "Country": null
                    }
                },
                "Currencies": {
                    "CurrencyCode": "ZAR"
                },
                "InterestDistribution": "",
                "NoticesBalance": 0,
                "AccountOpenDate": "2021-07-01T22:00:01Z",
                "CumulativeNoticesAmount": 0,
                "InstantAvailableNoticeBalance": 0,
                "MinimimAmountLimit": 0,
                "loggedOnUser": {
                    "UserFirstName": "John",
                    "UserLastName": "Doe",
                    "UserCompany": "John Doe (Pty) Ltd"
                },
                "NoticeInterestNominated": 0,
                "NoticeInterestBank": "",
                "noticeInterestAccountName": "",
                "NoticeInterestAccount": "",
                "PreviousStatementPeriod": "2023-01-01T22:00:01Z",
                "DebitAccountNumber": "",
                "DealReference": "",
                "AutomaticPaymentOrder": "0",
                "BackOfficeCustomerCode": "JDCARD",
                "AccountId": "10111",
                "AccountName": "10011111111 Credit Card",
                "AccountFullName": "",
                "AccountType": "Credit Card",
                "AccountTypeId": "1",
                "AccountNumber": "10011111111",
                "AlternativeAccNo": "",
                "ElectronicAccountNumber": "",
                "Balances": {
                    "CapitalBalance": 100,
                    "AvailableBalance": 100,
                    "PrincipalAmount": 0,
                    "ValueDate": "2023-01-01T22:00:01Z",
                    "ClosingBalance": 200,
                    "PendingCardBalance": 0
                },
                "BackOfficeType": "",
                "Products": {
                    "StartDate": "0001-01-01T00:00:00",
                    "EndDate": "0001-01-01T00:00:00",
                    "OverdraftLimit": 0,
                    "MaxTransferLimit": 0
                },
                "Description": "Credit Card",
                "OwnerType": "1",
                "Interests": {
                    "Amount": 0,
                    "Rate": 0,
                    "RateMaturity": 0,
                    "RateCredit": 0,
                    "RateDebit": 10,
                    "AccruedCreditInterest": 0,
                    "AccruedDebitInterest": 0
                },
                "ActiveFlag": "Y",
                "NickName": "Credit Card",
                "CreatedDate": "2021-07-01T22:00:01Z",
                "ModifiedDate": "0001-01-01T00:00:00",
                "MaturityAmount": 0,
                "StatementFrequency": "",
                "StatementNumber": "",
                "StatementDay": "0",
                "StatementMonth": "",
                "EmailAddress": "",
                "Category": "Borrow",
                "LinkedAccount": "",
                "AccountFormat": "4"
            }
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

That’s it!

Now you know how to pull data from the Investec API. You can discover several other endpoints in the [API reference](https://developer.investec.com/za/api-products), they all authenticate in the same fashion..

In the next step, we will explore how to push data to the Investec API and effect account changes.&#x20;
