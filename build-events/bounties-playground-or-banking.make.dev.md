# 💰 Bounties Playground | banking.make.dev

## What is this about?

We created [a central repo](https://github.com/programmable-banking-community/banking.make) as a community space for playing with programmable banking, and building/extending its API functionality. We hope that **anyone interested in building useful financial tools can use this repo to increase functionality for personal and business use-cases**.

## What do I need to know?

### The Bounties

{% hint style="warning" %}
✨**Bounty Season #1: 27 October to 14 November 2022** ✨
{% endhint %}

We have a list of bounties for functionality that we think will be useful to add to the current codebase.

* 👉 Check out these [available bounties as a starting point](https://github.com/programmable-banking-community/banking.make/issues?q=is%3Aissue+is%3Aopen+label%3Abounty)!

**What do I do when I find a bounty I like?**

* If you see one that you like,&#x20;
  * comment that you want to claim it.&#x20;
  * The person that created the bounty will respond with a "**go-ahead 👍**".
* You can [clone the GitHub repo](https://github.com/programmable-banking-community/banking.make) and work on your local machine.

{% hint style="info" %}
💡 **ProTip:** We recommend [forking our REPL on Replit](https://replit.com/@OfferZenMake/programmable-banking) for a quick-start. Replit is a great dev tool that makes it easy to run and edit code.
{% endhint %}

* Write the necessary code or documentation in your fork.
* Create a pull request into the main GitHub repo with your changes.
* Once your code is merged into the master app, you'll receive your bounty reward. 🏆

**Where do I get support?**

* Great question! Drop into the [dedicated bounties Slack channel here](https://offerzen-community.slack.com/archives/C048GPNT49W).&#x20;
* We'll be more than happy to help with any questions or support around your bounties build/ the bounties in general/ or if you want to hang out and help others.

{% hint style="info" %}
💡 **ProTip:** If you learn something interesting while working in the codebase, be sure to add it in ./knowledge so everyone can benefit!
{% endhint %}

### Other features

**Feel free to extend this app with other programmable banking features you'd like.** We can't guarantee it'll be merged into the main branch, but if it provides real value, there's a good chance it will be. Please make sure your code is well documented and its reason for existing is explained well.

### Issue tracking

[Report any issues on GitHub](https://github.com/programmable-banking-community/banking.make/issues/new)

### Getting set up

* Fork the code - either from this [REPL directly](https://replit.com/@OfferZenMake/programmable-banking) or [from GitHub](http://github.com/programmable-banking-community/banking.make/issues/new) if you prefer to work locally
* Configure the app's components to point to the domain your REPL is hosted at
  * Set the `DOMAIN` secret, the default is `banking.make.dev` - this is used in the root code compiler, among others
  * Update the connector file in `public/Investec.swagger.json` and replace `banking.make.dev`
* `npm install` and `npm start` ('_I think, not sure - I just use Replit and it auto-boots_')

### Current Features

#### Investec API

* `routes/investec.js` proxies any incoming `GET` and `POST` requests to the Investec API while converting API keys into single-use bearer tokens. The app doesn't store any sensitive information.
* `routes/investec/auth.js` contains middleware to extract partition information from API keys, if the requester is using partitioned access and `routes/investec/card_partitions.js` contains config for those partitions
* `routes/investec/special.js` extends Investec API base functionality by providing an abstraction layer for card control, handling card events, and simplifying the transfer endpoint

#### RootCode card control

* `modules/root_code_card_policy.js` converts simple config flags into a JS bundle that can be compiled as RootCode onto a supported card

#### Power Automate

* There is a connector file in `public/Investec.swagger.json` that you can import into [Microsoft Power Automate](https://make.powerautomate.com) or any other low-code tool
* `modules/power_automate.js` handles pubsub subscriptions for PowerAutomate events
* `routes/investec/special.js` contains several routes specific to Power Automate

## FAQs

1. **Can >1 person work on/request to work on a bounty at the same time? How is the decision about who works on it made?**
   1. Anyone can go after any bounty - it just depends on who commits first with all the criteria.
2. **Is there any time frame for the bounties to be completed in?**
   1. Yes, there is. There are Seasons - 3 weekends per bounty season.
3. **What is the engagement model once someone has started working on a bounty?**
   1. You can either work on their own and commit for approval as is, or they can join the Slack channel for support and book a "build session" with a community champion.
4. **What if the person cannot complete the bounty?**
   1. Then they don’t complete. We’ll make a call after each season to either roll over any unclaimed bounties and add new ones for the next seasons.
