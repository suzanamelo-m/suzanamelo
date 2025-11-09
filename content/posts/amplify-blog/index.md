+++
date = '2025-11-09T21:34:17+02:00'
draft = false
title = 'From Procrastination to Publishing: How AWS Amplify Helped Me Finally Start Blogging'
tags = ['Tutorial', 'AWS Amplify', 'Hugo', 'Cloud Computing', 'AWS']
+++

![AmplifyArticleBanner](/img/AmplifyArticleBanner.png)

Who doesn’t have an unfinished side project buried somewhere in a folder, notebook, or GitHub repository?

If you just nodded yes, keep reading. You’re in the right place! 🫂

---

## 💡 How it all started

I must admit, my list of unfinished side projects is long, and blogging was one of those ideas that kept coming back, with a few failed attempts added to the pile, even though I really wanted to make it happen.

Changing careers to software development after my 40s, as an immigrant woman with no tech background, was not easy, and it still isn’t. So, feeling that pain on my own skin, I decided to support others who are fighting the same battle.

I started speaking at and supporting local meetups, and before long, I became an organizer myself. But I soon realized that talks alone couldn’t reach everyone who might need help. So, I started writing. From dev tutorials to career-change insights, my articles were scattered across different platforms and never published as often as I wanted.

I knew it was time to create one place to call home for my content, and I set a goal to build my own blog.

---

## 😵‍💫 Under the “overwhelmed” feeling

Every time I tried to start this project, I found myself overwhelmed with questions:

- What programming language should I use?
- Do I need a framework? Which one?
- Where should I host it? What are the costs?
- How do I handle CI/CD, SSL/TLS, and DNS?

![Overwhelmed](/img/suzana-overwhelmed.png)

Soon enough, my prototypes in JavaScript, React, and Next.js joined the pile of side projects sitting in my GitHub repositories.

---

## 🌟 The light at the end of the tunnel

It kept happening until I finally did what I always tell my mentees: _Struggling? Ask for guidance!_</br>
That’s when I realized I didn’t need to reinvent the wheel.

[Allen Helton](https://www.linkedin.com/in/allenheltondev/), AWS Hero and dear friend, shared his fantastic [article](https://www.readysetcloud.io/blog/allen.helton/how-to-build-your-blog-with-aws-and-hugo/), **_“Take the Leap! 10 Steps to Building Your Personal Blog With AWS + Hugo,”_** and that’s when my blog dream started coming true.

---

## 🧩 What is Hugo?

![Hugo Logo](/img/hugo-logo.jpeg)

[Hugo](https://gohugo.io/) is an open-source static site generator that makes it incredibly easy to bring your ideas to life.

It offers multilingual support, great documentation, and can be used to build everything from documentation and landing pages to corporate, nonprofit, or event websites.

One of my favorite parts is the vast collection of customizable themes to help you get started quickly. Hugo also offers flexibility for hosting and deployment, including AWS Amplify.

---

## ⚡️ And what’s AWS Amplify?

![Amplify Logo](/img/AmplifyLogo.png)

The name really fits. [AWS Amplify](https://aws.amazon.com/amplify/) helps you build scalable, full-stack applications fast, without needing deep cloud expertise.

It’s a perfect solution for frontend and mobile developers who want to amplify their project’s capabilities and integrate AWS services without managing the complexities of cloud infrastructure.

Amplify offers features like Hosting, Backend Development, UI Components, DataStore, Analytics, APIs, Functions, Geo, AI, and Storage, all easy to add to your project.

What I loved most was how Amplify removed the technical friction that always overwhelmed me. Things like managing storage, CDN distribution, building pipelines, and SSL/TLS certificates.

---

## 🪚🔨 Building a static website

Even a simple blog involves several steps: preparing your HTML, CSS, JS, and assets; uploading them to a hosting service; and ensuring everything loads smoothly over the internet.

Behind the scenes, you need to link your repository, build static assets, handle the Domain Name System (DNS) to find the server’s IP address (so it can respond to the HTTP request from the browser by sending the requested static files), and distribute your content globally through a CDN, often managed via CI/CD pipelines.

If you’re using AWS, you’d usually deal with services like **S3 Buckets**, **Route 53**, **CloudFront**, and **AWS Certificate Manager**.

---

## 💞 Hugo & Amplify: the love story

Using Hugo and [AWS Amplify Hosting](https://aws.amazon.com/amplify/hosting/) together was refreshingly simple — a true tech love story.

When hosting a static site on Amplify, you let it take care of everything you’d otherwise configure manually. Your code is stored, distributed globally, secured with HTTPS, and automatically updated with each commit, all without you having to manage the infrastructure.

Amplify Hosting provisions:

- **Amazon S3** → stores and serves your static files.
- **Amazon CloudFront (CDN)** → distributes your site globally with low latency and high availability.
- **AWS Certificate Manager** → provides free HTTPS (TLS/SSL) certificates.

Amplify also integrates with **CloudWatch** and **CloudTrail** for monitoring, logging, and auditing, so you can easily track performance and activity.

And since Amplify is serverless, you only pay for what you use, and it's always ready when you are.

---

## 👩🏻‍💻 Building my blog — Step by step

### From Hugo's side

Now that we’ve covered the whys and whats, let’s get to the best part: _the building!_

---

### 1️⃣ Choose a theme

First, I picked a [Hugo theme](https://themes.gohugo.io/) (many include their own documentation that complements the Hugo guides) and started building the foundation of my blog — content and assets like articles, photos, and images.

Hugo offers a wide range of themes to suit different styles and needs. You can customize them by changing the default color palette, fonts, and layout, or even build your own from scratch.

---

### 2️⃣ Set up Hugo

Hugo’s [Getting Started](https://gohugo.io/getting-started/) documentation gives you everything you need to begin. The [Quick Start](https://gohugobrasil.netlify.app/getting-started/quick-start/) guide does an excellent job walking you through project setup: installing Hugo, adding content, building the site, and publishing it.

![Hugo commands explanation](/img/hugo-commands.png)

The [Basic Usage](https://gohugo.io/getting-started/usage/) guide explains how to use Hugo’s command-line interface (CLI) to perform basic tasks, and the [Directory Structure](https://gohugo.io/getting-started/directory-structure/) provides an overview of the project skeleton that Hugo generates when you create a new site.

![Hugo site skeleton](/img/hugo-site-structure.png)

Hugo uses Markdown for content files, which made it easy to organize my articles in the `content/` folder and store images in `assets/`.

![Blog structure](/img/blog-structure.png)

I gathered my previous articles from [Dev.to](https://dev.to/suzanamelo) and [LinkedIn](https://www.linkedin.com/in/suzanamelo-m/recent-activity/articles/), added images and logos, and tagged everything so readers can find content easily in one place.

![Editing in VS Code](/img/vscode-article.png)

---

### 3️⃣ Host and Deploy

Once I was happy with my site, it was time to host it. Using Amplify was seamless thanks to Hugo’s [Host on AWS Amplify](https://gohugo.io/host-and-deploy/host-on-aws-amplify/) guide.

**What I needed:**

- An AWS account (new customers can start with $100 credits through the [AWS Free Tier](https://aws.amazon.com/free/)).
- A GitHub (or other Git provider) account.
- A local and remote repository for my project.

Hugo provides an `amplify.yml` file with build commands that Amplify automatically runs during deployment, including installing Hugo, configuring Git, and building the site.

**amplify.yml**

```yml
version: 1
env:
  variables:
    # Application versions
    DART_SASS_VERSION: 1.93.2
    GO_VERSION: 1.25.3
    HUGO_VERSION: 0.152.2
    # Time zone
    TZ: Europe/Oslo
    # Cache
    HUGO_CACHEDIR: ${PWD}/.hugo
    NPM_CONFIG_CACHE: ${PWD}/.npm
frontend:
  phases:
    preBuild:
      commands:
        # Create directory for user-specific executable files
        - echo "Creating directory for user-specific executable files..."
        - mkdir -p "${HOME}/.local"

        # Install Dart Sass
        - echo "Installing Dart Sass ${DART_SASS_VERSION}..."
        - curl -sLJO "https://github.com/sass/dart-sass/releases/download/${DART_SASS_VERSION}/dart-sass-${DART_SASS_VERSION}-linux-x64.tar.gz"
        - tar -C "${HOME}/.local" -xf "dart-sass-${DART_SASS_VERSION}-linux-x64.tar.gz"
        - rm "dart-sass-${DART_SASS_VERSION}-linux-x64.tar.gz"
        - export PATH="${HOME}/.local/dart-sass:${PATH}"

        # Install Go
        - echo "Installing Go ${GO_VERSION}..."
        - curl -sLJO "https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz"
        - tar -C "${HOME}/.local" -xf "go${GO_VERSION}.linux-amd64.tar.gz"
        - rm "go${GO_VERSION}.linux-amd64.tar.gz"
        - export PATH="${HOME}/.local/go/bin:${PATH}"

        # Install Hugo
        - echo "Installing Hugo ${HUGO_VERSION}..."
        - curl -sLJO "https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.tar.gz"
        - mkdir "${HOME}/.local/hugo"
        - tar -C "${HOME}/.local/hugo" -xf "hugo_extended_${HUGO_VERSION}_linux-amd64.tar.gz"
        - rm "hugo_extended_${HUGO_VERSION}_linux-amd64.tar.gz"
        - export PATH="${HOME}/.local/hugo:${PATH}"

        # Verify installations
        - echo "Verifying installations..."
        - "echo Dart Sass: $(sass --version)"
        - "echo Go: $(go version)"
        - "echo Hugo: $(hugo version)"
        - "echo Node.js: $(node --version)"

        # Install Node.js dependencies
        - echo "Installing Node.js dependencies..."
        - "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci --prefer-offline || true"

        # Configure Git
        - echo "Configuring Git..."
        - git config core.quotepath false
    build:
      commands:
        - echo "Building site..."
        - hugo --gc --minify
  artifacts:
    baseDirectory: public
    files:
      - "**/*"
  cache:
    paths:
      - ${HUGO_CACHEDIR}/**/*
      - ${NPM_CONFIG_CACHE}/**/*
```

---

### 🔗 Connecting the dots

**Create a new app** — In the Amplify console, I clicked **Create a new app**.  
![Amplify create app](/img/amplify-create-app.png)

**Choose a Git provider** — I connected my GitHub repository.</br>
Amplify supports other providers such as GitLab, Bitbucket, and CodeCommit, as well as manual deployment from S3 or ZIP files.  
![Amplify select repo](/img/amplify-select-repo.png)

**Authorization** — I authorized the connection, selected my account (my personal account), and picked the repository I wanted to connect to.

> **Least privilege** — Amplify also allows connecting to all repositories, but best practice is to apply the principle of least privilege and grant access only to the specific project you’ll use.

---

### ✨ How the magic happens

Once everything was connected, I reviewed the settings and clicked **Save and Deploy**, and that was it!

Amplify compiles your code, installs dependencies, runs your tests (if any), and provisions the infrastructure needed, creating roles and app/branch resources behind the scenes.

It built and deployed my blog’s static assets automatically. From that point on, every GitHub push triggers Amplify’s CI/CD pipeline, which rebuilds and redeploys the site for me.

---

## 🌍 Route 53

Amplify gives you a default domain, but I wanted a personal one — **suzanamelo.com** — which I registered with [Route 53](https://aws.amazon.com/route53/).

![Route53 domain](/img/route53-domain-generic.png)

The process was simple, using the [AWS guide for adding a custom domain](https://docs.aws.amazon.com/amplify/latest/userguide/to-add-a-custom-domain-managed-by-amazon-route-53.html).

I went to **Custom domains** in the **Hosting** section on the sidebar, clicked **Add domain**, and as I started typing, my domain already appeared. Amplify shows all the domains you have through Route 53.

![Add your domain](/img/route53-add-your-domain.png)

You can also add a [custom domain managed by a third-party](https://docs.aws.amazon.com/amplify/latest/userguide/to-add-a-custom-domain-managed-by-a-third-party-dns-provider.html) DNS provider.

By default, Amplify automatically creates two subdomain entries for your domain —  
[`https://suzanamelo.com`](https://suzanamelo.com) and [`https://www.suzanamelo.com`](https://www.suzanamelo.com) — which you can customize. You can either use the default managed SSL/TLS certificate Amplify provisions for you or a custom third-party certificate imported into AWS Certificate Manager.

![Subdomain certificate](/img/route53-subdomain-certificate.png)

---

## 🚀 Why I think Amplify was great

Using Hugo with Amplify was perfect for my needs. It was quick to connect, effortless to deploy, and handled all the heavy lifting — monitoring, CI/CD, DNS setup, SSL/TLS, and global content delivery through CloudFront.

If you collaborate with others, Amplify also supports **feature branches**, **branch password protection**, and **pull request previews**, which is great for teamwork and testing before merging.

---

## 🤔 When Amplify may not be the best option

Amplify was perfect for _my_ use case — a simple blog — but it’s not a one-size-fits-all tool.

It’s beginner-friendly with lots of ready-to-use solutions, and very opinionated, which means it may not suit projects that require heavy customization, complex backend configurations, or deep infrastructure control.

Amplify shines for solo developers and small teams who want to ship fast and abstract away AWS complexities.

Speaking of beginner cloud-friendly… Keep in mind that you won’t really learn cloud infrastructure deeply if that's your goal. Amplify does that work for you so that you might miss out on that hands-on experience.

I also found its documentation a bit challenging at first (not surprising if you’ve used AWS docs before!). Having a mentor can really help when you hit confusing points.

---

## 💸 Pricing

If you’re testing a new idea like a blog or an MVP, you’ll likely stay within [AWS Free Tier](https://aws.amazon.com/free/)'s $100 credits for new accounts, which is what I used for my blog. You get 6 months to experiment, and the credit balance automatically applies to your bills once you move to a paid plan.

The [Amplify Pricing](https://aws.amazon.com/amplify/pricing/) page includes examples, like a startup with five developers committing twice a day and 300 daily users, costing about **$8.08/month**. Pretty great for what you get!

![Amplify Pricing](/img/amplify-pricing-example.png)

---

## 🎉 Wrapping up

With just a few clicks, I made my dream come true and launched **[suzanamelo.com](https://suzanamelo.com)** — a home for my articles on cloud, software development, career change, and soft skills.

I loved the whole experience. Using **Hugo + AWS Amplify** made everything so much easier than I expected. I got my project up and running super fast, with no time to feel overwhelmed.

Of course, it doesn’t replace the deeper learning that comes from configuring every single service and building your own infrastructure from scratch (and I highly recommend doing that at least once if you want to really understand what’s happening under the hood).

But if your goal is to test ideas, experiment, or launch an MVP, I’d absolutely use Amplify Hosting again, and I totally recommend a bit of **_ClickOps_** for these cases. It’s the perfect combo for moving fast and seeing results right away.

I’d love to hear your feedback, ideas, or suggestions for new topics. Have you tried hosting something on Amplify? Let me know. I’m always curious to hear other builders’ stories.

I hope this article helps you finally get that side project out of your “someday” folder and into the world. 💫

![Suzana Melo Blog Logo](/img/suzana-melo-blog-logo.png)

---

## 📝 Resources

- **Article** - [“Take the Leap! 10 Steps to Building Your Personal Blog With AWS + Hugo.”](https://www.readysetcloud.io/blog/allen.helton/how-to-build-your-blog-with-aws-and-hugo/) - [Allen Helton](https://www.linkedin.com/in/allenheltondev/)
- **AWS Amplify** - [Host a Static Website](https://aws.amazon.com/getting-started/hands-on/host-static-website/)
- **AWS Amplify** - [Hosting](https://aws.amazon.com/amplify/hosting/)
- [Adding a custom domain managed by Amazon Route 53](https://docs.aws.amazon.com/amplify/latest/userguide/to-add-a-custom-domain-managed-by-amazon-route-53.html)
- **AWS Amplify** - [Add a custom domain managed by a third-party DNS provider](https://docs.aws.amazon.com/amplify/latest/userguide/to-add-a-custom-domain-managed-by-a-third-party-dns-provider.html)
- **AWS Amplify** - [Pricing](https://aws.amazon.com/amplify/pricing/)
- **AWS** - [Free Tier](https://aws.amazon.com/free/)
- **AWS** - [Route 53](https://aws.amazon.com/route53/)
- **Hugo** - [Themes](https://themes.gohugo.io/)
- **Hugo** - [Getting Started](https://gohugo.io/getting-started/)
- **Hugo** - [Quick Start](https://gohugobrasil.netlify.app/getting-started/quick-start/)
- **Hugo** - [Basic Usage (CLI)](https://gohugo.io/getting-started/usage/)
- **Hugo** - [Host on AWS Amplify](https://gohugo.io/host-and-deploy/host-on-aws-amplify/)
