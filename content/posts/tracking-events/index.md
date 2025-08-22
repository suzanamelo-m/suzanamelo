+++
date = '2023-08-18T23:34:17+02:00'
draft = false
title = 'Tracking events effectively in Web Browsers with Mini Digital'
tags = ['Programming', 'Tutorial', 'Web3']
+++

![Mini Digital Banner](/img/ConnecWallet.png "Mini Digital Banner")

> Note: The product used in this tutorial is no longer available. Mini Digital was decommissioned.

Knowing your user's behaviour is life-changing for your product. It will give you insights to empower your product team to develop better solutions for your customers bringing benefits such as increasing fidelity and engagement and attracting new users.

Mini Digital comes into the market by offering a lightweight and privacy-focused library for collecting event data for product analytics from your entire stack: websites, web apps, mobile, backend services and decentralised apps, including sub-domains.

All in one solution. Bingo!

However, a tool is useless if you don’t know how to use it correctly.

Knowing how to track your data effectively is crucial for gaining the insights you need to plan and improve your products or marketing strategy.

This article will cover how to effectively integrate Mini Digital into your web browser using the SDK for accurate and insightful product tracking and what places you need to be in mind in your codebase to send your event data properly and achieve the desired outcomes.

---

## **Onboarding** 📝

For this article, let’s assume that the onboarding process has already happened with Mini Digital. This means you already have an account, and the Mini Digital team have set their configurations to receive the events from your domain and subdomains.

If you are reading this article in the future, Mini Digital App will already be available, and the onboarding will be straightforward. Using the app, you can sign in, create your account and quickly set up your domains and subdomains.

---

## **The Library** 📚

[Mini Digital SDK](https://github.com/WunderbarNetwork/mini-digital-sdk-js) is an open-source library built using TypeScript and the ESM module format, and it compiles to the ES2022 target. You can use it in Node.js or browser-based TypeScript/JavaScript projects (including frameworks like React or Vue). Backwards CommonJS compatibility is provided by the library.

---

## **Installation and use** 💻

Based on the [Mini Digital Docs](https://docs.mini.digital/), there are two main ways to track an event using Mini Digital and send your event payload to the Mini Digital API endpoint: using the SDK or submitting the raw payload with the required fields from the schema to the Mini Digital endpoint by HTTP request. I will cover this last option in another article, but you can find all information you need in the [docs](https://docs.mini.digital/event-tracking-integration/http-api.html).

First, you must install the SDK using a package manager (either npm or yarn). To do that, run the following:

```bash
npm install @wunderbar-network/mini-digital-sdk
```

or

```bash
yarn add @wunderbar-network/mini-digital-sdk
```

The next step is to import the SDK to your project, destructuring the AnalyticsEvent type and EventTrackingService module.

If installed via a package manager, you can import it as so (TypeScript/ESM syntax):

```bash
import { type AnalyticsEvent, EventTrackingService } from "@wunderbar-network/mini-digital-sdk";
```

If referencing a file (either from the CDN or locally), you can import it as per the example below:

```bash
import { type AnalyticsEvent, EventTrackingService } from "../lib/mini-digital-sdk.v1.3.esm.js";
```

Now that you have the SDK ready to go, this is the moment to declare your events for tracking.

---

## **Declare and send events** 📤

Once your initial set-up is done, it is time to think about what you want to track and, most importantly, where you will declare and send events to track the user behaviour you need.

The Analytics Event for the Mini Digital API Server expects a schema containing fields with properties to be supplied by the SDK consumer.

Mini Digital SDK provides pre-defined core schemas designed to keep your data consistent. Some are mandatory to keep the minimum information necessary for accurate tracking. There are also options for you to customise the data you want to send.

You can find more about Mini Digital Core Schema Properties [here](https://docs.mini.digital/core-schema/properties.html).

I will cover all the aspects and properties of the schema in the upcoming articles. In this article, let’s focus on the minimum mandatory fields you must fulfil, especially the use cases and best places for each event category in your codebase.

### **Mandatory properties** ✅

```typescript
const event: AnalyticsEvent = {
  eventName: "home_page_viewed",
  eventCategory: "screen_view_event",
  eventSource: "Website.MiniDigital.Router",
  entityType: "home_page",
  action: "viewed",
  anonymousUser: true,
};
```

**`eventName`**

This is crucial information for you to send when tracking an event. This property is a string that refers to the event name you are tracking, e.g., account_created, crown_minted, screen_viewed.

> Note: Mini Digital Docs recommends you define your eventName by using the object+action framework, where the object is the system or service that the user interacts with, e.g., button, screen or a data entity (account, image, payment, etc.), and the action is the verb that describes how the user/system interacted with the object, e.g., clicked, created, viewed, etc.

Mini Digital also includes optional properties that cover objects and actions and help you to define your `eventName`.

`entityType` - Type of the entity or object this event relates to (e.g. "account", "crown", "IPFS resource", etc.).

`action` - refers to the action that this event represents in past-tense verbs (e.g. "visited", "created", "minted", etc.).

**`eventCategory`**

This property will drive most of our examples in this article. It can be one of the five categories below, and understanding its user cases is fundamental for accurate event tracking:

- `screen_view_event` - It tracks when users navigate to a page/screen.
- `user_outcome_event` - It tracks when a user has completed a significant action in the product (e.g. when a user completes sign-up or uploads a file).
- `system_outcome_event` - It is used when an event happens within the system and is not immediately initialised by the user (e.g. when a scheduled task gets completed or a backend system has performed an action). Note: I will not cover examples of this user case in this article as I’m focusing on web browser integration, but remember that you can use this property to track events when they catch the server side.
- `interaction_event` - It tracks events when users interact with UI elements (e.g., the user clicks a button ou in a link).
- `content_event` - It tracks content that was interacted with (It is designed for more specific media (images, videos) or visual assets (logos, icons) than generic UI elements such as a button or a link - see `interaction_event` for those use cases).

**`eventSource`**

This property refers to the area in the product or source where this event occurred (e.g. "Website.WunderbarNetwork.Router", “AccountSettings”).

### **Anonymous user - a quick highlight** 💡

The cherry on top of Mini Digital is its anonymous user property by default, which significantly minimises your privacy policy and makes many web3 users feel relieved. This subject is so relevant that it deserves its own article, but there is an important aspect to cover here related to the two following properties of the [Core Schema](https://docs.mini.digital/core-schema/properties.html) that will inform the SDK about the user acting: `primaryIdentifier` and `anonymousUser`.

`primaryIdentifier` and `anonymousUser` are marked as optional in the `AnalyticsEvent` interface. However, at least one needs to be supplied.

There is a third property that also plays a vital role in this relationship, which is `trackingId`.

To understand the relationship between these three properties, let’s follow the behaviour of a user visiting a store website. In the first moment, when the user hits the store's landing page, and this event is tracked, you usually don’t know who the user is. This is when you include the `anonymousUser` property in your schema and set the field value as `true`.

Mini Digital SDK generates a `trackingId` (a random UUID) and makes the `primaryIdentifier` the same as the `trackingId`.

Suppose the user performs logging in and gets identified by the system (for example, by providing their username or customer number or after connecting using a wallet). In that case, you may want to replace the `anonymousUser` with the `primaryIdentifier` and fill the field with the identifier data. The same `trackingId` field will be attached to all events before and after that moment and can be used to link the actions performed before and after logging in, so you know that it is the same user all the time along.

---

## **Use cases by `eventCategory`** 🖊️

Now that you have all the pieces of the game you need, it is time to start to play.

Let’s again follow the journey of a user visiting a store website to understand a bit more about how and where to track your event while developing your integration to the SDK.

**`screen_view_event`**

The first action of a user in your product is usually navigating to a landing/homepage page.

An effective way to track when a user hits a screen/page is when the page renders for the first time, like this example below of a website's homepage being mounted in a Vue.js app. You will also want to set `eventCategory` to `screen_view_event`.

```typescript
onMounted(async () => {
  // Define event data for the homepage screen view
  const event: AnalyticsEvent = {
    eventName: "home_page_viewed",
    eventCategory: "screen_view_event",
    eventSource: "Website.MiniDigital.Router",
    entityType: "home_page",
    action: "viewed",
    anonymousUser: true,
  };

  // Send data to track when a user navigates to the homepage
  await EventTrackingService.postEvent(event);
});
```

**`interaction_event`**

It’s common to expect a user to explore a website before deciding to log in. Tracking how the user interacts with the website UI (User Interface) – clicking buttons and links or expanding sections, can provide your product team with helpful insights on how they can best improve the website. Tracking the **Login** button clicked, in addition to how the user interacted with the website before login, allows the team to have a complete picture of the user journey.

There are so many things your product team can do once armed with those insights. Suppose they notice that more people see the homepage than log in, and then the team creates a motivating fidelity points system. However, product teams can only plan improvement actions if they get the data. Otherwise, it will be only a guess. A dangerous land to walk on!

You can track this event category by sending your data when the user clicks the button and setting your `eventCategory` to `interaction_event`.

In my example below, I have a function called `handleConnectWallet()` to handle an event when the user clicks the button to connect their wallet. If successful, a list of accounts will be displayed, and the user can choose the one they want to use to connect their wallet.

```typescript
async function handleConnectWallet(): Promise<void> {
  // Define event data for Connect Wallet button clicked
  const event: AnalyticsEvent = {
    eventName: "connect_wallet_button_clicked",
    eventCategory: "interaction_event",
    eventSource: "Website.MiniDigital.Router",
    entityType: "connect_wallet_button",
    action: "clicked",
    anonymousUser: true,
  };

  // Send data to track when a user connects to a wallet
  await EventTrackingService.postEvent(event);

  // Load account list
  await checkForWeb3Accounts();

  // If no accounts, show error
  if (accountList.value.length === 0) {
    throw new Error(
      "No web3 accounts could be found. Please check your extension(s) and try again."
    );
  }
}
```

**`content_event`**

When you want to be even more specific about the content that the user interacts with, the `content_event` property comes in handy to give even more accurate insights to your product team. It is designed to track more specific media (images, videos) or visual assets (logos, icons) than generic UI elements such as a button or a link.

Where to declare it depends much on your codebase and the context where your image, logo, or icon is used - if it is a video played by the user or a banner used as a link and handled by a function like the above. However, you also want to send your event data when the user interacts with the content.

```typescript
const event: AnalyticsEvent = {
  eventName: "mini_digital_banner_clicked",
  eventCategory: "content_event",
  eventSource: "Website.MiniDigital.Router",
  entityType: "mini_digital_banner",
  action: "clicked",
  anonymousUser: true,
};
```

**`user_outcome_event`**

Our last example to explore is when the user completes a significant action in the product, and our user just performed a login in our store website by choosing an account and connecting with their wallet. At this moment, all the validations were performed, and the login is successful.

In my example, I have a function that handles the successful login, sends my event data to Mini Digital and takes my user to another page that he can only access once logged in.

This is when you want to send your event data with your `eventCategory` set to `user_outcome_event`. Also, this is when the business may decide to use the identifier provided by the user. Logins are a perfect example of actions performed that allows you to update your schema by removing the `anonymousUser` and setting your `primaryIdentifier` to the identifier provided by the user.

```typescript
async function handleWalletAccountConfirmed(
  walletAccount: WalletAccount
): Promise<void> {
  // Save the selected account to our state management tool
  await store.commitWalletAccount(walletAccount);

  // Define event data for account successfully logged
  const event: AnalyticsEvent = {
    eventName: "wallet_account_logged",
    eventCategory: "user_outcome_event",
    eventSource: "Website.MiniDigital.Router",
    entityType: "wallet_account",
    action: "logged",
    primaryIdentifier: store.walletAccount?.address,
  };

  // Send data to track wallets successfully logged
  await EventTrackingService.postEvent(event);

  // Navigate to the dashboard
  await router.push({ path: "/dashboard" });
}
```

Note now that my user is not anonymous. I have stored my user’s identifier detail and used it to provide a value for `primaryIdentifier`.

---

## **Closing up** 💌

In this article, I covered how to install and import Mini Digital SDK to start integrating the SDK into your codebase. I explained how to declare and send the events using the minimum information necessary for accurate tracking. I also provided examples of what mandatory properties you must send, the perfect timing, and where to declare your event schema.

I hope this article helped you better understand how to track your events most effectively to empower your product team with accurate insights.

I look forward to your feedback, and stay tuned for more articles. 👋🏻
