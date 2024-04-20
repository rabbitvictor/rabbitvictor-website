+++
title = 'Building a personal blog with Hugo and Cloudflare Pages'
date = 2024-04-19
draft = false
+++

##  Why am I creating this blog?

I always enjoyed talking about my interests and lately I've lacked peers to talk about some of these interests,
mainly the ones related to computer science and engineering.
I know it sounds cliché, but as a New Year's resolution, I decided to start writing about these interests.

In particular, I'm a software engineer, so it feels natural to start a blog about my learnings in programming languages, web development fundamentals and computer science in general. Recently I stumbled upon the idea of [learning in public](https://www.swyx.io/learn-in-public), and it aligns a lot with my expectations for this blog. Also, I do believe in having independent websites — the Internet these days feels monopolized by the big guys — Reddit, Google, Meta, TikTok, and the like making it feel small, and I love the idea of having my own little piece of the internet to talk about anything.

Without further ado, let's get to the main topic at hand: the technologies used to create this blog itself!
##  Hugo
I'm definitely not a front end developer, so the choice for a static site generator (SSG) was obvious to me. I was torn between [Hugo](https://gohugo.io/) and [Jekyll](https://jekyllrb.com/), but ended up choosing Hugo because I really liked the [Blowfish](https://blowfish.page/) theme and the simplicity it offered. I do enjoy writing in Markdown and the flexibility it gives me, so this was another point in favor of SSGs.

Furthermore, I followed [Blowfish's initial setup](https://blowfish.page/docs/getting-started/) and read some of the [Hugo documentation](https://gohugo.io/documentation/) to familiarize myself with the framework. Not only that, but I had the initial version of the website up and running in a couple of hours — really easy to set up! I can recommend Hugo for anyone that wants a nice looking blog without having to spend too much time making it look nice — the framework has a thriving community with countless [themes to pick from](https://themes.gohugo.io/).

After that, it was really easy to customize the theme to my liking — I'm looking for something that is low maintenance and easy to use, and I find that Hugo + Blowfish gives me all that after the set-up is done.

##  Cloudflare Pages
The next problem was the hosting and deployment of the website. I had already bought the www.rabbitvictor.com with [Porkbun](https://porkbun.com/) as the registrar, and I needed some place to host it, preferably for free. [Cloudflare Pages](https://developers.cloudflare.com/pages) fit the bill perfectly; I discovered it because their S3-compatible object store [R2](https://developers.cloudflare.com/r2/) caught my attention, as well as their Cloudflare Workers, which is a serverless compute service.

Anyway, with Cloudflare Pages, you can deploy a website with a multitude of frameworks entirely serverless, using Cloudflare infrastructure to distribute and host it for you. Even more than that, they offer an [automated deployment](https://developers.cloudflare.com/pages/framework-guides/deploy-a-hugo-site/#deploy-with-cloudflare-pages) of your website with a GitHub integration; every push to the `main` branch of your git repository triggers a deployment, it is really cool! This integration also creates [preview deployments](https://developers.cloudflare.com/pages/configuration/preview-deployments/) on PRs, so you can check out how the site will look like after the changes in a live environment. 

They had a [guide]() for the Hugo framework that I followed, and it went smoothly; very well writing documentation. There are guides for a lot of frameworks, here is a [link](https://developers.cloudflare.com/pages/framework-guides/) to see all the options.

##  The experience so far
I had the idea of a blog for a while now, but never pulled the trigger because I thought it would be a lot harder to create and maintain; but after setting up Hugo, creating a blog post is done by a single command `hugo new content posts/foo-bar`. Markdown is a nice writing format, as mentioned before. I can test the layout locally with `hugo server` and when I'm ready to deploy, it is as simple as pushing a new commit to `main` and Cloudflare Pages takes care of the rest. It makes creating blog posts more about the creative and writing process and less about technical details. Don't get me wrong, I love technical details! But my goal for this was to make this blog set up frictionless, opening up space for the technical details in other projects.

## Next steps
First of all, thank you for reading this blog post! Feel free to contact me about any questions or comments about this article. I'm looking forward to filling up this website with my learnings, projects and experiences. Until next time!