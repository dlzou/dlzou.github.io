---
layout: post
title: A Beginner's Roadmap to Computer Science
tags:
- computer science
- research
- commentary
categories:
- Blog
date: 2021-5-15 00:00:00 -05:00
---

{% include image.html url="/assets/img/bike-road-bluescreen.jpg" href="https://www.deviantart.com/alltelleringet/art/Road-Closed-Unexpectedly-810362448" caption="Credit: @alltelleringet on DeviantArt" %}

Before I stepped into college, I didn't think computer science was much more than writing code, but the last two years have shown me just how wrong I was. What are some cool fields to pursue? What background knowledge is involved? Though I'm admittedly still a novice compared to the grizzled verterans in industry and academia, I'd still like to tackle these questions with my current knowledge, for the benefit of younger me and those like him.

CS is such a diverse and interconnected field that it's hard to include everything in one coherent post, but I'll do my best to cover what I know, organized by topic.


### Algorithms

This is the most general definition I can give: algorithms are steps that one can take to solve specific problems. Algorithms are why computers exist in the first place, and they're in everything that runs the modern world. 

The most traditional algorithms are **deterministic algorithms**; this means the order and input to all the operations in our algorithm are the same every time we run it. An example for the well-known problem of sorting of list of items is [merge sort](https://en.wikipedia.org/wiki/Merge_sort). Deterministic algorithms are great in many cases, but we might get problems that are too complicated or datasets that are too big to handle, and moreover, we often don't need the *exact* or *best* answer to some problem, only an answer that's good enough. Hence, **approximation algorithms** and **randomized algorithms** are becoming hot areas of research. 

{% include image.html url="/assets/img/merge-sort-example.gif" caption="A visualization of merge sort" %}

Developing an algorithm requires us to analyze the structure of a specific problem and come up with creative solutions. In addition, an algorithm is only useful if we can make guarantees about its correctness, runtime, and space usage. Deriving all of this involves a lot of math, such as [combinatorics](https://en.wikipedia.org/wiki/Combinatorics), [logic](https://en.wikipedia.org/wiki/Logic), [graph theory](https://en.wikipedia.org/wiki/Logic), and [probability](https://en.wikipedia.org/wiki/Probability). These are all interesting practical fields that are rarely taught in high schools.


### Machine learning

In recently years, a new class of algorithms called **machine learning (ML)** have taken the world by storm. With ML, we can approach many problems that seem hard to define or quantify, like "what object is in this picture" or "what other songs might this person like." ML models are less about reasoning, and more about data. When a model is training, it's essentially "guessing" relationships in some dataset to help it make predictions in the future, and this is done with techniques from statistics and optimization. 

{% include image.html url="/assets/img/obj-detect-cam.gif" caption="View from an object detection algorithm" %}

ML is often considered a subfield **artificial intelligence (AI)**, but I think a distinction should be made. My perspective is that AI refers to a framework for representing various "intelligent behavior" like decision-making and perception, and ML is just one approach to it. AI has had an interesting history of periods of hype followed by [periods of disinterest](https://en.wikipedia.org/wiki/AI_winter), and it is also the source of many social and ethical debates. Maybe it'd be interesting to do a deeper dive of this subject in a future post.


### Systems


### Wait, what about...

"Do I still need a CS degree if my goal is to write apps?"

Consider how you're reading this post right now. The pixels that you see are rendered by geometry-based graphics algorithms. Data, like text and pictures are sent to your device by fast communication algorithms that also check for errors. The servers and networks sending this data also need to handle countless other requests, and they optimize this with---you guessed it---algorithms. And that's just an immediate example; from big data to scientific computing to financial systems, there's an unquenchable need to compute things quickly and accurately.
