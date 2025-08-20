+++
date = '2023-06-08T23:34:17+02:00'
draft = false
title = 'Three things I loved most about Next.js 13.4 so far'
tags = ['react', 'nextjs', 'programming']
+++

# Three things I loved most about Next.js 13.4 so far

![Next JS](/img/nextjs.png)

Next.js was first launched in October 2016 by Vercel (formerly Zeit), years before I started programming. However, I only started learning it about a month ago when I needed to develop an application as part of a technical challenge using the famous “React framework”.
Its latest version, Next.js 13.4, brought a lot of upgrades and changes on top of what already exists.
I don’t intend to delve deeply into those changes here - you can easily find plenty of good articles already discussing features, but I wanted to highlight what was my “love at first sight” from a newbie perspective, with no preference order.

### Learning curve 📚

As an immigrant woman who changed careers and entered the software development field after my 40s with no technical background, learning technology remains very challenging, especially when it is something I see for the first time. Although my love for programming and learning new things makes the process more pleasant and easier, it does not necessarily make things easier.
However, I was surprised by how much easier it was to understand Next.js' logic and structure, which is built on top of React, providing extra features that I found very handy. The documentation is also easier to follow and understand.

### New Project 💻

Next 13.4 offers you TypeScript and TailwindCSS by default, which is fantastic. I’d decided to use TypeScript to build a side project, but you can also use JavaScript or JSX. It is up to you.
I learned software development by doing a bootcamp that utilized JavaScript as its core programming language. Although I used TS for a few months in a startup I previously worked with, it is still very challenging for me, and I love it.
To start to play around with the latest version of Next.js, run the following command to create a new project (you will also need to have Node.js 16.8 or later):

`npx create-next-app@latest`

You will be asked these prompts before putting your hands on the code.

```
What is your project named? my-app
Would you like to use TypeScript with this project? No / Yes
Would you like to use ESLint with this project? No / Yes
Would you like to use Tailwind CSS with this project? No / Yes
Would you like to use `src/` directory with this project? No / Yes
Use App Router (recommended)? No / Yes
Would you like to customize the default import alias? No / Yes
```

#### Structure

Once the project is ready and you open it on your IDE (I use Visual Studio Code), you will have a structure like that:

![New Project](/img/newproject.png)

To see it in your _localhost:3000_, start up the dev server by running the following:

`npm run dev`

## Love number 1: Routing ❤️

As per Next.js documentation.

> In version 13, Next.js introduced a new App Router built on React Server Components, which supports shared layouts, nested routing, loading states, error handling, and more. The App Router works in a new directory named app. The app directory works alongside the pages directory to allow for incremental adoption.

**What does it mean?**
Creating a route in Next.js 13 is ridiculously simple.
Inside the `app` directory/folder, you have a `page` file (in my case, _page.tsx_), which is your app homepage. Inside that main app directory, create a folder with the name of the route you want, and inside that `route/folder`, create a file called `page.tsx`.

![Main page file](/img/mainpagefile.png)

Here, I created a route to an About page by creating a directory called `about` and a `page.tsx` inside it. In the `page.tsx` file, I included an arrow function component that returns a title and content.
If you repeat these steps and go to _localhost:3000/about_, you will see the text content from the AboutPage component, as I did. And that is all you need to do. Easier like that!

![About page](/img/about.png)

Note that folders are used to define _routes_, and files are used to create the UI for that route. The folder's name is the _route_, and its file is called `page.tsx`.

#### Nested routes

To create nested routes, you need to repeat the same steps, but this time in the route folder. In my example, I implemented a route for `/about/team` by creating a folder called `team` inside the `about` folder. In the `team` folder, I created a new `page.tsx` file displaying a title and content. Once saved, the content of TeamPage was rendered on _localhost:3000/about/team_.

![Nested route](/img/nestedroute.png)

Of course, my project side is minimal and straightforward. Big and complex projects will demand a planned folder distribution and structure, but from my learning curve perspective, creating a route in Next.js was very easy to understand and execute.

## Love number 2: Layout ❤️

Another great feature of Next.13 that I loved is the layout.
As per Next.js,

> A layout is UI that is shared between multiple pages. On navigation, layouts preserve state, remain interactive, and do not re-render.

When you create your new Next.js project, the `layout` file is also included next to the main `page.tsx`. It is a simple React component where you can add a header, footer, and any other content you want to appear on every page.

![Layout](/img/layout.png)

As you can see in the image above, this is also where you will include your _metadata_, such as title, description, keywords, and so on.

```
export const metadata = {
  title: 'Create Next App',
  description: 'Generated by create next app',
}

```

You can also easily include fonts from Google. The layout provided in your initial project consists of an example of importing Google fonts straightforwardly.
You just need to import the font you want and store it in a variable like that:

```
import { Inter } from 'next/font/google'

const inter = Inter({ subsets: ['latin'] })
```

You can also add other attributes you need for your project. Here is another example:

```
import { Poppins } from 'next/font/google';

const poppins = Poppins({
  weight: ['400', '600'],
  subsets: ['latin'],
});

```

To apply the font to your project, simply add the className to the tag you want to use it on. The Next.js boilerplate applies the className to the body of the project:

```
  return (
    <html lang="en">
      <body className={inter.className}>{children}</body>
    </html>
  )

```

#### Nested layouts

As per Next.js documents, Layouts can also be nested.
You can customise a layout for a specific page by adding a new layout file in the folder you want.

Here is how Next.js docs illustrate an example:

![Nested layout](/img/nestedlayout.png)

Let’s go back to the About page I mentioned previously. I can create a different layout for that page by creating an `about/layout.tsx` file next to my `about/page.tsx`. In this file, I defined a React component:

```
export default function AboutLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    <>
      <div>{children}</div>
    </>
  );
}

```

Your creativity (or the project requirements) is the limit. You can include a new font or metadata in your custom layout, or you may want a different container, a sidebar, or any other layout you need for your project.

My thought on this feature is that I was guided by a fantastic senior to keep my CSS files at the same level as their respective files. Having everything in the main styles folder would quickly become very messy and make it harder to coordinate changes from a maintenance perspective in the future. Next.js, applying the same concept with the nested layout file, made a lot of sense.
You can read more about pages and routing on this [page](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts) of Next.js docs.

## Love number 3: Server Components ❤️

This feature took me the most time and effort to understand, but once I grasped the concept, it looked fascinating and full of opportunities for experimentation and learning.

As per Next.js docs, let’s quickly highlight two crucial definitions of this feature.

> The client refers to the browser on a user's device that sends a request to a server for your application code. It then turns the response from the server into an interface that the user can interact with.

> The server refers to the computer in a data center that stores your application code, receives requests from a client, does some computation, and sends back an appropriate response.

NextJS 13 includes a Server Components feature by default, and as per its documents:

> “allowing you to render components on the server easily and reducing the amount of JavaScript sent to the client.”

**What does it mean?**
Servers can process JavaScript and create documents faster than a client.
For Server Side Rendering, your service response to the browser is the HTML of your page, ready to be rendered. It will start rendering the HTML from your server without waiting for all the JavaScript to be downloaded and executed, the opposite of what happens on the Client Side Rendering.

I followed Next.js recommendations for fetching data in Server Components.
I tried simple data fetching, and I found it to be easier and straightforward.

✔️ Here is what I did:

- I created a Server Component called Repos to render my repositories on GitHub.
- Created an async function called `getRepos()` and used the Next.js `fetch()` API - you can learn more about it on the [Next.js docs](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) - to get the data I wanted from the GitHub API and fetch it straight away in the component.
- I called the `getRepos()` and returned the details I needed to display, such as the name and description of my GitHub repositories.

![Fetch](/img/fetch.png)

### Last thoughts 📌

I just started diving deep into this exciting framework, and I loved the experience of playing around with Next.js.
It has downsides, and there is a lot to explore and learn from.

- Server Components are less interactive than Client Components.
- They can’t be a component state, and you can’t use the `useState` hook.
- It also doesn’t support lifecycle methods, and you can’t use the `useEffect` hook, which is handy for a component where you need to keep re-rendering, e.g., a search component.
- If you want to use the `useState` hook and make it interactive, you need to make it a Client Component by adding _‘use client’_ to the top of the component, but I’m going to leave this step for another day.

Still, many developers in the community are already excited about these new features, as they can combine some of the interactive experiences of client-side apps with the improved performance of traditional server-rendered applications.
Server Components improve the initial page loading time, simplify data fetching, and improve access to databases and file systems.

As I mentioned, these thoughts are from my perspective and take into account my ongoing learning process, which is constantly evolving.

If you're already familiar with Next.js, I would love to hear your insights on the new features and what I can experiment with. If you are new to that, like me, I hope I've piqued your curiosity to try and share your thoughts. 🚀
