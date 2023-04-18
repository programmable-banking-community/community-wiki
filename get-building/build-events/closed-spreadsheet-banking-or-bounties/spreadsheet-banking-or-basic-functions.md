---
description: Working with Spreadsheet Banking in Excel
---

# 👩💻 Spreadsheet Banking | Basic Functions

## How to:

* [Reference a table ](spreadsheet-banking-or-basic-functions.md#how-to-reference-a-table)
* [Fetch a single table column ](spreadsheet-banking-or-basic-functions.md#fetching-a-single-table-column)
* [Do calculations on a table ](spreadsheet-banking-or-basic-functions.md#doing-calculations-on-a-table)
* [Do complex filtering with tables and live-sync](spreadsheet-banking-or-basic-functions.md#complex-filtering-with-tables-and-live-sync)

{% hint style="success" %}
**If there are other functions that you use and would like to share, please feel free to** [**contribute to the page here**](../../../build-events/spreadsheet-banking-or-bounties/spreadsheet-banking-or-basic-functions.md) **or** [**pop us a mail**](mailto:community-investec@offerzen.com)**, and we'll add it.** ❤️
{% endhint %}

{% embed url="https://www.loom.com/share/ec2e375d8f2e4a9ca68a0c14c680f4e4" %}
An intro to working with Excel tables and formulas in Spreadsheet Banking.
{% endembed %}

### **How to reference a table**

**✨** Reference your accounts: `tblAccounts`&#x20;

**✨** Reference your transactions: `tblTransactions`

### **Fetching a single table column**

#### Functions for Accounts/Transactions

> **Requirement:** I want to reference my ID for all my transactions.

```
Function: =tblTransactions[ID]

=tblTransactions[ID]
=tblTransactions[AccountNumber]
=tblTransactions[Date]
=tblTransactions[Description]
=tblTransactions[Debit]
=tblTransactions[Credit]
=tblTransactions[Balance]
```

{% hint style="info" %}
**\***Sub in Accounts to see account information
{% endhint %}

#### **Transforms on functions**

> **Requirement:** I want to show you the first two letters of my transaction description.

```
Function: =left(tblTransactions[Description],2)
```

### **Doing calculations on a table**

#### **Calculations on functions**

> **Requirement:** I want to see a sum of all my transactions coming off my account.

```
Function: =sum(tblTransactions[Debit])
```

#### **Fetching table headers**

> **Requirement:** I want to see what the headers of my table are.

```
Function:=tblTransactions[#Headers]
```

### **Complex filtering with tables and live-sync**

#### **Filtering within your transactions/Accounts**

> **Requirement**: I want to filter the description of all my transactions only displaying the first two letters.

```
Function: =(left(tblTransactions[Description],2)
```

> **Requirement: \`**I want to filter the description of all my transactions only displaying the first two letters for a specific account.

```
Function: =(left(tblTransactions[Description],2), tblTransactions[Account Number]=Playground!B4
```

> **Requirement:** I want to filter the of all my transactions greater than R5000 for a specific account.

```
Function: filter(tblTransactions[Debit]),(tblTransactions[Account Number]=Playground!B4)*(tblTransactions[Debit]>5000)
```

#### **Search Term**

> **Requirement**: I want to filter all my transactions for my account that contain the search term ‘Uber’ (Uber in cell D17) using the first 4 letters of the description.

```
Function: tblTransactions[[Description]:[Debit], left(tblTransactions[Description],4)=D17
```

