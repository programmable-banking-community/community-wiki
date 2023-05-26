# 💰 How to simulate a transaction

On the right hand side of the code editor you will see the simulator. This allows you to simulate transactions to test out the code on your card before you deploy it. Once you have simulated a transaction, you will be presented with the `simulation.json` file which will explain what has happened in the transaction.

![](https://lh6.googleusercontent.com/jemxlBNuf6XqYXnwjc0nsD29ZY-SFqF3awv0437f345YRcxongar6Db3Z-Ozhx00KvlA32aNS7OeRoENg8aomnunucInLzvbIqhzwQt2FMJmXmm0Wg\_doIfb9o9YUN-uAMhCjnxgWrm2Lb5FQOLHcpw)

In the above simulation you can see that the simulated transaction has failed because the amount of R55 (5050 cents) was over the limit specified in the code snippet.

Once you are happy with your code and have tested it out, you may deploy your changes to your card using the “Deploy code to card” button.

{% hint style="info" %}
**Pro-Tip:** The `log.json` file shows all the logs from the code. You can also log certain outcomes using the `console.log` function.
{% endhint %}
