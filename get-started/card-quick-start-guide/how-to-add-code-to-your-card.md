# 🖥️ How to add code to your card

{% embed url="https://www.loom.com/share/d7f710df6e4e4b00b4cc7967907829ce" %}

There are three main functions that can be used to execute custom functionality on your card:

* **beforeTransaction** - Every time you initiate a transaction from your Investec card, the beforeTransaction method intercepts the authorization object before it is approved by Investec. This gives you the ability to apply logic to either decline or approve the transaction based on data from the card authorization itself. This function needs to return a true or false value in order for it to work. Time is limited for this function so use minimal code.
* **afterTransaction** - This function will execute after every transaction that has been processed by the card and it runs after the `before_transaction` function.&#x20;
* **afterDecline** - This function will execute if a transaction has been declined on the card.

Once you have enabled your card for Programmable Banking, select the desired card by clicking on the image of the card and you will be presented with the following online editor.

![](https://lh4.googleusercontent.com/wII4bQlHtKCDVkHrZQ1bPP2ReIkGNeISpTbixeaGTghp9Uxc04fEtOa1bgi5IKE5kR\_Elytz6TtDomNfkZ3EoKmYoybrzANFjfWvBJsXdIg6EuWkV0zgLTfxPQu\_P\_9S1qPJZDyMv7zS-ytQk8RuUOY)

{% hint style="info" %}
**Pro-Tip:** The IDE can be slow to load and you might need to refresh the page.
{% endhint %}

The file which you will be working on the most is the `main.js` file that is open in the screenshot above. To test out adding code to your card, you can paste the following code snippet into the `main.js` file as shown below. The code snippet declines card purchases that are made in bakeries (using a specified merchant code) and that are over R50 (or 5000 cents). You can add the code snippet to the `main.js` file and it won’t have any effect on your card until you click “deploy code to card”.

{% hint style="info" %}
**Pro-Tip:** When referring to amounts in the code it is the cent value of the transaction. R55 equals 5500 cents.
{% endhint %}

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
