+++
date = '2026-05-19T15:34:15+02:00'
draft = false
title = 'Bedrock vs SageMaker: a beginner’s guide to AWS AI — and where to start'
tags = ['Amazon Bedrock', 'Amazon SageMaker', 'Generative AI', 'AWS', 'AI for beginners']
+++

![BedrockSagemaKerGuideBanner](/img/bedrock-sagemaker-banner.png)

You've started your AWS journey. You're hearing about AI everywhere, and two names keep coming up: Bedrock and SageMaker. Everyone seems to assume you already know what they are.

You don't. And that's completely fine — I didn't either.

In this article, I'll give you a clear overview of both services, explain which one makes more sense to start with, and show you where you can get hands-on experience with both at no cost.

---

📌 **Before we go further:** </br>
If you're an absolute beginner to Cloud and AWS, I recommend reading ["How to get started with AWS (for absolute beginners)"](https://suzanamelo.com/articles/aws-for-absolute-beginners/) first and coming back when you're ready. These concepts will land much better with that foundation in place.

---

## Bedrock and SageMaker — what are they, exactly?

Both are fully managed AWS services designed to help you build, customise, and deploy AI and machine learning (ML) applications.

Either Bedrock or SageMaker gives you:

✨ Access to cutting-edge Foundation Models (FMs) (including Anthropic Claude and Meta Llama), with pre-trained, ready-to-use options  
✨ Features to tailor models to your specific needs, such as fine-tuning and Retrieval-Augmented Generation (RAG), which lets you connect models to your own data sources  
✨ Seamless integration with other AWS services

But the similarities end there. They are not competitors. Bedrock and SageMaker solve different problems and operate at very different levels of abstraction.

---

## Thinking in layers

When working with AI on AWS, it helps to picture the stack in layers:

- **Infrastructure layer** → where models are built and trained
- **Model access layer** → where pre-trained models are accessed and used
- **Application layer** → where AI features are integrated into products

SageMaker sits closer to the infrastructure layer. Bedrock sits closer to the application layer. Keep that in mind as we look at each one.

---

## Amazon Bedrock

![Amazon Bedrock console](/img/bedrock-console.png)

[Bedrock](https://aws.amazon.com/bedrock/) is a serverless platform designed from the ground up to make generative AI accessible, with pre-trained models available as ready-to-use options. It gives you access to powerful foundation models via API, with no model training required.

Instead of building models from scratch, you:

- Choose a model (Claude, Titan, Llama, and others)
- Send prompts via API
- Get responses back

The biggest advantage is speed: no infrastructure to manage, fast time to production, and you only pay for what you use (your API calls).

Bedrock is ideal when you don't have ML expertise but want to build quickly (chatbots, AI features inside apps, rapid prototypes).

Imagine a customer support assistant that answers questions from your product documentation, a content tool that drafts marketing copy on request, or an internal search feature that understands natural language instead of keywords. These are all problems Bedrock handles well. You describe what you want, pick a model, and start building.

**If you find yourself thinking, _"I just want to use AI, not build it,"_ Bedrock is your starting point.**

---

## Amazon SageMaker AI

![Amazon SageMaker console](/img/sagemaker-console.png)

[Amazon SageMaker AI](https://aws.amazon.com/sagemaker/ai/) (formerly Amazon SageMaker) is a full machine learning platform with fully managed infrastructure, tools, and workflows. It gives you everything you need to:

- Prepare and process their own datasets
- Train models from scratch
- Fine-tune existing models with proprietary data
- Deploy, monitor, and manage model performance over time

Where Bedrock is about speed and simplicity, SageMaker is all about control and customisation. You manage the full ML lifecycle, which means more power and more complexity. It's worth mentioning that Bedrock does support fine-tuning for a limited set of models, but it's a managed, lightweight process (very useful for adjusting a model's tone or style). SageMaker gives you full control over the training process, including custom training scripts and complete access to model weights, which is what you need when the task genuinely requires it.

It's the right tool when you need custom ML pipelines, are working with proprietary datasets, or your team has dedicated ML expertise. Picture a hospital building a readmission risk model on its own patient records, a manufacturer predicting equipment failures from sensor data, or a legal team training a classifier on thousands of labeled contracts. These are real-world problems SageMaker is built for, where an off-the-shelf model won't do, and full control over the training process matters.

**If you find yourself thinking, _"I need to understand exactly how my model works,"_ SageMaker is your platform.**

---

## Can they work together?

Yes, and in many real-world architectures, they do.

A common pattern: use Bedrock to prototype quickly and validate whether an AI feature is worth building. Once you've validated the idea, then bring in SageMaker when you need to fine-tune, optimise performance, or take full control of the model. You're not choosing one forever. You're choosing which one fits the problem in front of you right now.

---

## Where to start as a beginner

If you've been following along, the answer is probably clear: **start with Bedrock.** 💡

It requires no infrastructure setup, lets you start building immediately, and removes enough complexity that you can focus on learning how AI actually behaves (rather than how to configure a training job). More than that, it gives you room to play around, get your hands dirty, and have fun breaking things along the way.

That said, don't skip SageMaker entirely. Understanding what it does, even at a conceptual level, gives you a much stronger mental model of how AWS AI services fit together. The stronger your foundation, the faster you'll move when things get complicated. And trust me, they will get complicated.

---

## Building your foundation for free

![AWS Skill Builder](/img/AWSSkillBuilder.png)

AWS offers a wide variety of free resources to get you started. My favourite platform for this is **[AWS Skill Builder](https://skillbuilder.aws/)**, where you'll find structured learning plans for Generative AI built to support different professionals and meet different needs: Developers, Decision Makers, Model Builders, Public Sector, EU Governments, and more.

![Generative AI Learning Plans](/img/genai-learning-plans.png)

📌 **On the question of cost:** Skill Builder has both free and paid content. The foundational courses are genuinely free, with no subscription needed. Some modules inside longer learning plans do require a paid subscription.

A great entry point for your AI journey is the **[Fundamentals of Generative AI](https://skillbuilder.aws/learn/FKXM21R555/fundamentals-of-generative-ai/ZFX96NREH4)** — 3 hours of free content covering:

- Fundamentals of ML and Generative AI
- Applications of Foundation Models and Amazon Bedrock
- Responsible AI
- Security, compliance, and governance for AI solutions

If you're already comfortable with programming, don't miss the **[Generative AI Learning Plan for Developers](https://skillbuilder.aws/learning-plan/5C9XQBTXBB/generative-ai-learning-plan-for-developers-includes-labs/EGATKJP13J)** — a full 20-hour structured path covering:

- Introduction to Generative AI — Art of the Possible
- Planning a Generative AI Project
- Amazon Bedrock Getting Started
- Foundations of Prompt Engineering
- Exploring Amazon Nova models using Amazon Bedrock
- Building Generative AI Applications Using Amazon Bedrock (Includes Labs) _(note: this module requires a subscription)_
- Amazon Q Developer Getting Started
- Introduction to Amazon SageMaker Notebooks

---

## Getting hands-on with Cloud Quest

![Cloud Quest Generative AI Practitioner](/img/cloud-quest-genai.png)

Theory will only take you so far. At some point, you just have to break something and have some fun, right?

That's exactly what **AWS Cloud Quest** is for. It's an online, open-world role-playing game where you learn cloud concepts by solving real-world problems (not through slides, but through actual tasks inside the AWS console). Honestly, it's as fun as it sounds.

If you're just getting started, begin with **[Cloud Practitioner](https://skillbuilder.aws/learn/FU5WCYVGKY/aws-cloud-quest-cloud-practitioner/JF9TKU68GT)**. It consolidates your foundational knowledge and gives you hands-on experience with core AWS services through real-life cloud challenges.

For Bedrock and SageMaker specifically, the one you want is **[Generative AI Practitioner](https://skillbuilder.aws/learn/5YB3FCEE1H/aws-cloud-quest-generative-ai-practitioner/26A81MG83V)**.

![Cloud Quest - Bedrock Playgrounds](/img/bedrock-cloud-quest.png)

Here you'll work through 10 real-world AI challenges. By the end, you'll know how to:

✨ Build AI-powered assistants (chatbots and virtual assistants)  
✨ Use Retrieval-Augmented Generation (RAG) to connect models to company data  
✨ Craft and optimise prompts for better model outputs  
✨ Choose between Foundation Models in Amazon Bedrock for different problem types  
✨ Apply guardrails and security principles for responsible AI

![Cloud Quest - Create an Enterprise Knowledge Assistant](/img/enterprise-knowledge-assistant.png)

What I liked most: I ended up working with not just Bedrock, but SageMaker and Amazon Q (AWS's AI assistant for development) across different challenges. The use cases were real — an HR assistant that filtered employee questions and pulled answers directly from the company handbook, and an enterprise tool that helped sales teams make sense of their own data. Building and running them changed how I understood these services.

By the time I completed the quest, the differences between Bedrock and SageMaker stopped being abstract. They made sense in practice, in a way that just reading about them didn't fully achieve.

![Cloud Quest - AI Services with SageMaker](/img/ai-services-sagemaker.png)

---

## More good resources out there

Skill Builder and Cloud Quest are my go-to starting points because they're free, structured, and built specifically for the AWS stack you'll eventually be working with. But they're not the only resources worth your time, and some of the best learning I've done on generative AI foundations has happened elsewhere.

### If you want to understand what generative AI actually is before you touch any tools

[Generative AI for Everyone](https://www.deeplearning.ai/courses/generative-ai-for-everyone) ([DeepLearning.AI](https://www.deeplearning.ai), free) — taught by AI pioneer [Andrew Ng](https://www.linkedin.com/in/andrewyng/), it covers how generative AI works, what it genuinely can and can't do, prompt engineering at a practical level, and how to think about real-world applications. No coding background required, no AWS account needed. I'd put this alongside the Fundamentals of Generative AI course on Skill Builder. They complement each other rather than overlap.

### If you want to build something before you feel "ready"

[PartyRock](https://partyrock.aws/) — an Amazon Bedrock playground where you can create AI-powered apps by describing what you want to build, no code required, with free daily usage. You don't even need an AWS account to start. It's the fastest way to develop real intuition about how foundation models behave, what prompts actually do, and where generative AI surprises you (for better and worse). Think of it as the place to play before Cloud Quest.

### If you want a structured course that lives outside Skill Builder

[AWS Generative AI Essentials](https://www.coursera.org/learn/aws-generative-ai-essentials) (Coursera and edX, free to audit, launched January 2026) — practical and applied rather than theoretical. It covers Amazon Q Developer for IDE-integrated coding assistance, Amazon Bedrock, RAG with private data, security guardrails, and building AI agents. A good structured step-up once you've worked through the Fundamentals course.

📌 **On cost — a consistent reminder across all three:** PartyRock has a free daily usage allowance. Generative AI for Everyone is free on DeepLearning.AI's platform. AWS Generative AI Essentials is free to audit on Coursera and edX (a certificate costs extra, but you don't need it to learn the material).

---

## Want to make it official? Certification is one option

![AI Practitioner Foundational Badge](/img/ai-practitioner-certi.png)

Once you've covered the fundamentals, if you want to make your knowledge official, the **[AWS Certified AI Practitioner](https://aws.amazon.com/pt/certification/certified-ai-practitioner/)** is worth considering. Still, it's one path among several, not an obligatory next step, and yes, Skill Builder has the preparation materials for that too.

That said, the broader generative AI certification landscape has grown significantly. If your interests point toward Google Cloud's stack, more developer-focused AI engineering, or perhaps toward AI for business and strategy rather than technical implementation, there are strong credentials in those directions too, such as the [Generative AI Leader](https://cloud.google.com/learn/certification/generative-ai-leader). The right certification is the one that aligns with where you're actually heading.

I haven't taken the AWS AI Practitioner exam yet, but when I do, I'll write up exactly how I prepared and what the experience was like.

If you've already been through it, I'd love to hear from you. What do you wish you'd known before you started? What helped? What would you tell someone who's just taking their first steps? Share your experience — your insight might be exactly what someone else needs to keep going. 💫

---

## Further reading & resources

### AWS-specific:

- [Amazon Bedrock](https://aws.amazon.com/bedrock/) - the official service page. Good for a high-level overview and feature list; not a learning resource on its own.
- [Amazon SageMaker AI](https://aws.amazon.com/SageMaker/ai/) — same: useful for orientation, not for learning how to use it.
- [Amazon Bedrock or Amazon SageMaker AI? — AWS Decision Guide](https://docs.aws.amazon.com/decision-guides/latest/bedrock-or-SageMaker/bedrock-or-SageMaker.html) — a more detailed comparison from AWS. Useful once you've absorbed the basics from this article, it assumes some familiarity with the services.
- [PartyRock](https://partyrock.aws/) — the no-code Bedrock playground. Start here if you want to experiment with models before writing a single line of code.

### Tutorials and hands-on:

- [Amazon Bedrock for Beginners — From First Prompt to AI Agent (Full Tutorial)](https://dev.to/aws/amazon-bedrock-for-beginners-from-first-prompt-to-ai-agent-full-tutorial-12ln) — a hands-on tutorial that picks up where this article leaves off. Good next step if you want to start building immediately.
- [Amazon Bedrock for Beginners — From First Prompt to AI Agent (Full Tutorial on YouTube)](https://www.youtube.com/watch?v=FAgmR9VV0GQ) — if you prefer video.

### Beyond the AWS stack:

- [Generative AI for Everyone](https://www.deeplearning.ai/courses/generative-ai-for-everyone) ([DeepLearning.AI](https://www.deeplearning.ai), free) — — the best non-AWS starting point for understanding generative AI conceptually. No coding required. Taught by Andrew Ng.
- [AWS Generative AI Essentials](https://www.coursera.org/learn/aws-generative-ai-essentials) (free to audit) — practical and applied; covers Bedrock, Amazon Q, RAG, and agents. A structured step up from Skill Builder's fundamentals content.
