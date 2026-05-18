+++
date = '2026-05-18T21:34:17+02:00'
draft = false
title = 'Bedrock vs SageMaker: a beginner’s guide to AWS AI — and where to start'
tags = ['Tutorial', 'Amazon Bedrock', 'Amazon SageMaker', 'Generative AI', 'AWS']
+++

![BedrockSagemaKerGuideBanner](/img/bedrock-sagemaker-banner.png)

You've started your AWS journey. You're hearing about AI everywhere, and two names keep coming up: Bedrock and SageMaker. Everyone seems to assume you already know what they are.

You don't. And that's completely fine — I didn't either.

In this article, I'll give you a clear overview of both services, explain which one makes more sense to start with, and show you where you can get hands-on experience with both at no cost.

---

📌 **Before we go further:** </br>
if you're an absolute beginner to Cloud and AWS, I recommend reading ["How to get started with AWS (for absolute beginners)"](https://suzanamelo.com/articles/aws-for-absolute-beginners/) first and coming back when you're ready. These concepts will land much better with that foundation in place.

---

## Bedrock and SageMaker — what are they, exactly?

Both are fully managed AWS services designed to help you build, customise, and deploy AI and machine learning (ML) applications.

Either Bedrock or SageMaker gives you:

✨ Access to cutting-edge Foundation Models (FMs) (including Anthropic Claude and Meta Llama), with pre-trained, ready-to-use options  
✨ Features to tailor models to your specific needs, such as fine-tuning and Retrieval-Augmented Generation (RAG), which lets you connect models to your own data sources  
✨ Seamless integration with other AWS services

But the similarities end there. They are also not competitors. Bedrock and SageMaker solve different problems and operate at very different levels of abstraction.

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

**If you find yourself thinking, _"I just want to use AI, not build it,"_ Bedrock is your starting point.**

---

## Amazon SageMaker AI

![Amazon SageMaker console](/img/sagemaker-console.png)

[Amazon SageMaker AI](https://aws.amazon.com/sagemaker/ai/) (formerly Amazon SageMaker) is a full machine learning platform with fully managed infrastructure, tools, and workflows. It gives you everything you need to:

- Prepare and process data
- Train models from scratch
- Fine-tune existing models
- Deploy and monitor performance

Where Bedrock is about speed and simplicity, SageMaker is all about control and customisation. You manage the full ML lifecycle, which means more power and more complexity. It's the right tool when you need custom ML pipelines, are working with proprietary datasets, or your team has dedicated ML expertise.

**If you find yourself thinking, _"I need to understand exactly how my model works,"_ SageMaker is your platform.**

---

## Can they work together?

Yes, and in many real-world architectures, they do.

A common pattern: use Bedrock to prototype quickly and validate whether an AI feature is worth building, then bring in SageMaker when you need to fine-tune, optimise, or take full control of the model. You're not choosing one forever. You're choosing which one fits the problem in front of you right now.

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

Skill Builder does have a paid subscription, but you don't need it to get started. All foundational course content is free — just enrol and learn. (If you see an invitation to subscribe when you first access the platform; you can safely skip it for everything covered here.)

A great entry point is the **[Fundamentals of Generative AI](https://skillbuilder.aws/learn/FKXM21R555/fundamentals-of-generative-ai/ZFX96NREH4)** — 3 hours of free content covering:

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

Working through it, I found myself using not just Bedrock, but SageMaker and Amazon Q (AWS's AI assistant for development) across different challenges. By the end, the differences between the services stopped being abstract. They made sense in practice.

![Cloud Quest - AI Services with SageMaker](/img/ai-services-sagemaker.png)

---

## Ready for the next step? Certification

![AI Practitioner Foundational Badge](/img/ai-practitioner-certi.png)

Once you've covered the fundamentals and want to make your knowledge official, the **[AWS Certified AI Practitioner](https://aws.amazon.com/pt/certification/certified-ai-practitioner/)** is the natural next step, and yes, Skill Builder has the preparation materials for that too.

I haven't sat the exam yet, but when I do, I'll write up exactly how I prepared and what the experience was like.

If you've already been through it, I'd love to hear from you. What do you wish you'd known before you started? What would you tell someone who's just taking their first steps? Share your experience in the comments — your insight might be exactly what someone else needs to keep going. 💫

---

## Further reading & resources

- [Amazon Bedrock](https://aws.amazon.com/bedrock/)
- [Amazon SageMaker AI](https://aws.amazon.com/SageMaker/ai/)
- [Amazon Bedrock or Amazon SageMaker AI? — AWS Decision Guide](https://docs.aws.amazon.com/decision-guides/latest/bedrock-or-SageMaker/bedrock-or-SageMaker.html)
- [Amazon Bedrock for Beginners — From First Prompt to AI Agent (Full Tutorial)](https://dev.to/aws/amazon-bedrock-for-beginners-from-first-prompt-to-ai-agent-full-tutorial-12ln)
- [Amazon Bedrock for Beginners — From First Prompt to AI Agent (Full Tutorial on YouTube)](https://www.youtube.com/watch?v=FAgmR9VV0GQ)
