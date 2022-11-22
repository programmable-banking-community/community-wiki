# 🚗 Card | How to create a DIY petrol card

## Purpose of this tutorial

Petrol cards are useful because they enable you to set a specified limit for spending on petrol, and you can monitor your fuel and motor expenses separately.&#x20;

* You already have a Programmable Banking enabled Investec card. So how can you use it for this purpose?

## The challenge

Now and again, Investec receives a request for **a card that only works at petrol merchants, either at the pumps or the service shop**. The ability to limit cards to a specific use is something that interests the Investec API team, and that is why they have put together a few simple steps to create your own DIY petrol card in the comforts of your own home.

* [ ] **Step 1:** Speak to your Private Banker about getting a specific card for this. You can even request a custom name to be embossed on it.
* [ ] **Step 2:** Once you have the card, ask your Private Banker to enable it for Programmable Banking.&#x20;
* [ ] **Step 3:** Go to the IDE on Investec Online to code it. Investec’s Head of Architecture for the API team, [Hennie Spies](https://za.linkedin.com/in/henniespies), has put together a code snip that will do all the hard work for you!

{% hint style="info" %}
**Pro Tip:** If you want to give the card to a specific person (e.g. for work), you will need to chat with your Private Banker about the FICA requirements on that card.
{% endhint %}

## Code snippet to include in your Investec IDE 👇

```javascript
//Merchant codes for fuel
//5499 : "Miscellaneous Food Stores - Convenience Stores and Specialty Markets"
//5541 : "Service Stations"
//5172 : "Petroleum and Petroleum Products"
//5542 : "Automated Fuel Dispensers"av
const fuelCodes = ["5499", "5541", "5172", "5542"];
 
const beforeTransaction = async (authorization) => {
    console.log(authorization);
    if (fuelCodes.indexOf(authorization.merchant.category.code) > -1)
        {
            return true;
        }
    return false;
};
 
// This function runs after a transaction.
const afterTransaction = async (transaction) => {
    console.log(transaction)
};
 
const afterDecline = async (transaction) => {
    console.log(transaction)
};
```
