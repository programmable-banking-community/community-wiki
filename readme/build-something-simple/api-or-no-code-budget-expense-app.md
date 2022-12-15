# 🎯 API | No-code Budget Expense App

## Purpose of this tutorial

This tutorial will show you how to set up the framework for a no-code/ low-code mobile budget expense app that can leverage your Investec’s Programmable Banking transactions with [Google Sheets](https://www.google.com/sheets/about/) and [Glide](https://www.glideapps.com/).

{% hint style="info" %}
🤩 The idea of doing it as a no-code/low-code challenge in 90 mins is not to get all fancy and technical. But to realise that **creating something with real-world implications is fun** - who knows - it might spark a cool idea for later! _**It’s just for funsies**_.&#x20;

\
**Share your progress/ final build** [**in Slack**](https://offerzen-community.slack.com/archives/C047HMLESSE) **- we would love to see how you’ve built on this further!**
{% endhint %}

### By the end of this build tutorial, you should be able to:

1. Explore what  Programmable Banking means,
2. Discover different ways to engage with your financial well-being,
3. Design a low-code budget expense app [Spike](https://medium.com/studio-zero/spikes-pocs-prototypes-and-the-mvp-5cdffa1b7367)

### Watch the whole build in realtime:

{% embed url="https://www.loom.com/share/b1c73f42d5b041d599daa9a265f0eaf6" %}
🌈 Pro Tip: Speed up the vid to get to the good bits.
{% endembed %}

### What you are going to need:

* Access to [Google Sheets](https://www.google.com/sheets/about/)
* About 90 min of your time
* Access to your [Investec API](https://www.loom.com/share/864ad2434b19417094efe647530d65eb) (_for later_)
* A free account on [Glide](https://www.glideapps.com/)

## The Job To Be Done:

* Create a mobile app where I can log expenses and track current budgets.
* Be able to identify which expenses are recurring.
* I can easily connect it to my Investec account to see expenses at a glance.

## 🌮 The super short version:

> **To create a mobile budget expense application using Google Sheets and Glide, follow these steps:**\
>
>
> 1. First, create a [Google Sheet](https://www.google.com/sheets/about/) to be the backend data storage for your budget expense app. In the sheet, create columns for the different types of expenses that you want to track, such as groceries, transportation, and entertainment.
> 2. Next, create a Glide account and sign in to the [Glide website](https://www.glideapps.com).
> 3. Click the "Create App" button to create a new app.
> 4. In the "Create an App" dialogue box, choose the "_Import a Google Sheet_" option and select the budget expense sheet you created in step 1.
> 5. Glide will automatically generate an app based on the data in your Google Sheets. You can customise the app by clicking on the different elements in the app preview and using the options in the right-side panel to change their appearance and behaviour.
> 6. Once satisfied with the app, click the "Publish" button to publish it.
> 7. Glide will generate a URL for your app that you can use to access it from any device. You can also download the Glide app from the App Store or Google Play and use it to access your app on your mobile device.\
>
>
> **Share your awesome build with the community in** [**#02\_make-it-happen**](https://offerzen-community.slack.com/archives/C047HMLESSE)**.** :sparkles:****

## 🌈 The long version:

### Step 1: Plan your route

Plan out what screens you want to see and how your data would be structured.

👉 Here is an [example on a Miro Board](https://miro.com/app/board/uXjVPT-ZfrI=/?moveToWidget=3458764536426296498\&cot=10).

### Step 2: Grab your gear

* Go to the [Build Something Simple](./) section in the community wiki&#x20;
* Copy that Google Sheet for Treasury Management&#x20;
* **Have a poke around the template. It’s a cool piece of work!**

{% hint style="success" %}
🐇 We can use the treasury management features in this sheet later when we add more features to our app - for now, we are just setting up the groundwork.
{% endhint %}

### Step 3: Build the (data) structure

* We are building the framework for a budget expense app, so let’s start thinking about the type of data we would like to use.
* Let’s start by creating two new sheets in our fancy new Workbook to use as a reference table in our app.
  * **App Items** (_These are budget expense apps we’ll be capturing_)
  * **App Cat** (_These are the categories we’ll use in our application_)

<figure><img src="../../.gitbook/assets/Screenshot 2022-12-15 at 10.15.45.png" alt=""><figcaption><p>🗂️ Create your sheets for Categories and Items</p></figcaption></figure>

* Let’s start putting in some data to work with _**App Cat**_.
  * Start with the categories you want to capture&#x20;
  * Maybe a cool emoji for easier reference?
  * And a budget limit for that category&#x20;
  * We can add pretty pictures later.
* In App Items, we can populate it with some dummy data for now.&#x20;
  * Name&#x20;
  * Cost&#x20;
  * Category & Icon (:bulb: **Pro Tip**: _We can copy\&paste from the category sheet_)&#x20;

### Step 4: Make the app data work

* Got to [Glide here](https://www.glideapps.com/)
* Create a new mobile app
* Connect to your Googe Sheets app It’s going to pull in all your sheets from the Workbook&#x20;
  * We only need our App Cat and App Items sheets for now.
* You can follow 📽️ t[his video to see how to add all the fancy reference tables](https://www.loom.com/share/b1c73f42d5b041d599daa9a265f0eaf6?t=317) and maths you’ll need to fully bring your app to life!
* Now that we have our data the way we want, we need a smart overview screen to bring everything together.
  * So let’s also 📽️ [create an overview dataset with fancy maths](https://www.loom.com/share/b1c73f42d5b041d599daa9a265f0eaf6?t=1017) like this.

