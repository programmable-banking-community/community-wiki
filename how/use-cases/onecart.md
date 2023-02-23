---
description: Fraud detection and prevention with Programmable Banking
---

# Onecart

[OneCart](https://www.onecart.co.za/) is a South African online delivery platform that enables customers to shop at a variety of retailers and have their purchases delivered to their door within hours. Making sure that their shoppers have sufficient funds on their cards and are spending appropriately is essential to OneCart’s operation.

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### The Problem: Detecting fraud and controlling shopper spend

The underbelly of online shopping is that someone has to go to a physical store, select the required items, pay for them at the checkout counter, and then deliver them to the client. To make this possible, OneCart shoppers are supplied with a bank card to pay for items. There is, however, inherent risk in giving employees direct access to company funds and OneCard found that shoppers were spending additional money on the cards. While OneCart could pick this up after the fact, recouping the losses was difficult.&#x20;

### The Solution: Programming card spend limits and real-time tracking&#x20;

Using [Investec Programmable Banking](https://www.investec.com/en\_za/banking/tech-professionals/programmable-banking.html), [Serverless](https://aws.amazon.com/serverless/), [Slack, ](https://api.slack.com/messaging/webhooks)and [QlikView](https://www.qlik.com/us/products/qlikview), OneCart now controls when, where, and how cards are used and keeps tabs on shopper transactions in real-time.\
They added a series of checks and balances before any transaction is approved:&#x20;

* Cards are only active during working hours.
* A merchant check ensures shoppers only use cards at partnered stores.
* The order amount is verified before each purchase.
* A deviation is built into the card limit to account for price differences between stores.

### Winning with Programmable Banking

* If a transaction check fails, an alert is sent via Slack Webhooks and the transaction can be investigated before shopper fraud can occur.
* OneCart can track in real-time how much money is coming in. After each swipe of the card, the transaction details are fed into a business intelligence tool that breaks down gross profit from each transaction.

**For OneCart, Programmable Banking has completely changed the game by solving an integral risk in their business model.**&#x20;

{% hint style="info" %}
Watch a demo of OneCart’s solution at our Programmable Banking community meet-up [here](https://www.offerzen.com/blog/onecart-using-programmable-banking-for-fraud-detection-and-prevention).
{% endhint %}

