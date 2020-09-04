---
layout: post
title: Hello World!
tags:
- meta
- web development
categories:
- Blog
date: 2020-08-25 16:00:00 -05:00
---

... As the CS tradition goes. Since this is my first post, it feels natural to start by explaining how this website came to be and what I'm going to do with it. "But it's just a portfolio website?" Yeah... but I have bit more in mind. Please, have a seat.


### What a Year

Let's begin with a big picture. 2020 has been one of the most chaotic years in recent history by many standards, and it's certainly *the* most chaotic year I've yet to live through. So much is happening in the world---pandemic, elections, disasters, protests---but sometimes there seems to be so little to do. Even though I'm lucky to not face any financial hardships, staying home so much still takes its toll over time. 

But lockdown hasn't been all doom and gloom for me; in fact, I've found that being alone with my thoughts is weirdly liberating in a way. Taking a step back from relentlessly regular routines has given me a rare chance to think about things that are usually beyond my field of view. And of course, our world in 2020 is in no short supply of such things. 

With plenty of problems to ponder and not much to do, I often find myself stuck in tangled thoughts. I could post more often on social media, but I'd rather not bombard my online friends with long rambles that are mostly about me. What's another outlet that gives me the freedom to post my random thoughts? A blog of sorts, perhaps...


### First Attempt

If you already know me, then this is no surprise, but [I like doing computer stuff](https://i.imgur.com/Hfzf14T.gif). Once I decided I was going to make a blog site, my first idea was to build a dynamic website with both a frontend (site) and a backend (server) because hey, why not hone my web development skills in the mean time? 

I had a great plan going in. I used [FastAPI](https://fastapi.tiangolo.com/), a high performance Python backend framework, combined with [SQLAlchemy](https://www.sqlalchemy.org/) for database management. I also wanted to dip my toes in frontend development and figured [Vue.js](https://vuejs.org/) would be approachable. 

I've never used any of these technologies before, but that's hardly an issue given the sheer number of tutorials and documentation online, many by the creators themselves. After a few weeks of on and off work, I had all the main components for a backend. But by this point, I was looking for better options.

As the name suggests, a dynamic web app has a lot of moving parts. Like any other software beyond simple scripts, it's one thing to get it working during development, and a whole different thing to make sure it *always* works when you leave it out in the "real world." In other words, 👻 **integration tests** 👻. Had I finished both the backend and frontend, I still must do testing and maintenance. And there's still deployment and the cost of getting a remote host. 

I still believe that the tools I used were some of the best. Impressively, all three projects I linked above were started by individuals who were motivated to make countless developers' lives easier while expecting nothing in return. I am grateful to them, and by extension, the entire open source community. The next time I work on a more ambitious web app, I may turn to these tools again. However, I admit they are overkill for a personal website.


### Building This Website

This whole time, I underestimated how powerful and ubiquitous static blogging has become. For the unfamiliar, static sites don't talk to a backend server, which means no forms, no live updates, etc. Static sites are light and fast, but they are considered less interactive than dynamic ones. Think: those plain HTML pages you come across while searching up a physics equation.

But it seems that I've been behind the curve, because new technologies and services are bringing more and more features to static sites. One of them is [Jekyll](https://jekyllrb.com/). Jekyll has everything I'm looking for---open source, content management system, built-in pagination, a cool vertical theme---and then some. It took me just one afternoon to set it up and play with some styling, and now it's hosted on [GitHub Pages](https://pages.github.com/), free of charge and free of upkeep. What difference the right tool makes.

By the way, shoutout to [@mdo](https://github.com/poole/hyde) and [@fongandrew](https://github.com/fongandrew/hydeout) for the fresh theme. 

(Might read like a sponsored message, but I pinky swear it's not)


### Plans For This Website

A main use of this website will be to show off some of my past and future projects. This format lets me informally share some insights that don't really belong in a README but are still relevant to my "journey." I also expect to leave some loosely organized thoughts here as they come, mostly to do with tech. Hopefully this will keep things interesting.
