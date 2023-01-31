---
layout: post
title: How I Put Up This Blog Site for Just Under an Hour
categories: [technology]
tags: [jekyll, tech, ruby, chirpy, github pages]
---

It's just fitting that my first post here in my site is how I put it up. Few years ago, if you asked me to put up a personal blog site, I might point you to either putting up your own wordpress site, or blogger site but now, a blog site built using JAMstack might be the best route for this.

Let me tell you how I put up this small, text centric blog site of mine, but no, this won't be a tutorial, but if you want to put up your own, probably this can be your starting point.

### Static Sites

What the hell is a static site? You might ask this if you're not familiar in the technicalities of how a website works. During the transition into Web2.0, websites are mostly interactive, one can also argue that apps right now are being prioritized to be accessible in web rather than building a native app. These interactive website, might be over simplfying it, is called dynamic sites, and they require servers and processing powers so users can access and interact with it. Static sites on the other hand are already built codes sitting on a web server and best for rarely changing informative content, like this blog.

### Jekyll and Github Pages

To make this site, I used [Jekyll](https://jekyllrb.com/), a simple static site generator. Jekyll allows you to create a static site with just Liquid templates, HTML, CSS and markdown files as your database, the best part? You can deploy this on [github pages](https://pages.github.com/) without paying for anything. Even if you don't know that much about frontend development, there's so many [prebuilt themes](https://jekyllthemes.io/) out there that you can use.

*You may also use any static website hosting platform out there. I recommend checking [Cloudflare pages](https://pages.cloudflare.com/)*

### Chirpy Theme

One of the best thing you can get out of using jekyll as your blogging platform is that there are so many built in themes that you can get for free. This site is using a free theme called [Chirpy Theme](https://chirpy.cotes.page/posts/getting-started/), a text centric theme that provides you probably everything you need. It also comes with already written deploy script for [github action](https://github.com/features/actions) that automatically build the app and deploy it on github pages.

If you're looking for a good guide to watch on how deploy this on your own, I recommend watching this [video](https://www.youtube.com/watch?v=F8iOU1ci19Q&t=1045s&ab_channel=TechnoTim)








