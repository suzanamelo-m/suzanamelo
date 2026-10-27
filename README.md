# Suzana Melo's Blog — Empowering Through Tech

![Suzana Melo Blog Logo](assets/img/suzana-melo-blog-logo.png)

**Cloud, AWS & AI for career changers and beginners.**

Live site: [suzanamelo.com](https://suzanamelo.com/)

## About

Suzana Melo is a full-stack engineer and AWS Community Builder who moved
into tech in her 40s, after 20+ years in journalism and media leadership
in Brazil. She founded [The Mentor Gap](https://thementorgap.org/), a free
initiative that creates resources for people growing without a mentor,
and for new mentors getting started.

She also founded the AWS Women's User Group Sweden, co-organizes the AWS
User Groups Skåne and Manaus and AWS Community Day Baltic, and mentors
career changers and women in tech through Women Innovating in Cloud Africa
(WIICA) and Escola da Nuvem. Her talks, workshops, and mentoring reach tech
communities across Europe, West Asia, Africa, Asia-Pacific, and the
Americas, in English and Portuguese. Suzana spoke at AWS re:Invent 2024,
is studying for a postgraduate specialization in AI and Machine Learning
at PUC Minas, and writes about cloud, AWS, and AI for developers and
career changers at suzanamelo.com.

- [LinkedIn](https://linkedin.com/in/suzanamelo-m)
- [GitHub](https://github.com/suzanamelo-m)
- [Sessionize](https://sessionize.com/suzana-melo/)
- [Bluesky](https://bsky.app/profile/suzanamelo.bsky.social)
- [Dev.to](https://dev.to/suzanamelo)
- [Instagram](https://instagram.com/suzana.melo.m)
- [Email](mailto:hello@suzanamelo.com)

## Tech stack

Built with [Hugo](https://gohugo.io/) and the
[Blowfish](https://blowfish.page/) theme (included as a git submodule),
deployed on [AWS Amplify](https://aws.amazon.com/amplify/). The Amplify
build pipeline installs Hugo Extended, Dart Sass, and Go directly
(see `amplify.yml`).

To run locally:

```bash
git clone --recurse-submodules https://github.com/suzanamelo-m/suzanamelo.git
cd suzanamelo
hugo server
```

## License

The site's code and configuration (Hugo config, layouts, build scripts)
are licensed under MIT, see [LICENSE](LICENSE). Reuse it as a starter
for your own Hugo + Blowfish + Amplify setup, with attribution.

The written content (blog posts, articles, and other original material
in `/content`) is not covered by that license and remains all rights
reserved, © Suzana Melo. Please do not republish or redistribute
without permission.
