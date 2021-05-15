---
layout: post
title: Computers and Humans
tags:
- computer science
- computer architecture
- commentary
categories:
- Blog
date: 2020-09-27 00:00:00 -05:00
---

I recently started learning [RISC-V](https://en.wikipedia.org/wiki/RISC-V) assembly in [CS 61C](https://www2.eecs.berkeley.edu/Courses/CS61C/), and I must say, getting closer to the metal has been a transformative experience. Sure, trying to write and debug assembly instructions as a beginner is painful, but it has given me incredible perspective. After years of coding, this may be the first time I'm truly wowed by computers... And even more so by humans.


### The Simplicity of Computers

Every high-level programming language I've come across has something in common: sprawling documentation, sometimes even from multiple sources ([looking at you C++](https://www.google.com/search?q=c%2B%2B+documentation)). So I was surprised to find out that the RISC-V reference can fit in a single sheet...

{% include image.html url="/assets/img/riscv-greencard.jpg" caption="The RISC-V green card" %}

My surprise went away as I dug deeper. In contrast to Python or Java, assembly languages are low-level, meaning they're program instructions designed to be read easily by machines rather than humans. Since machines are no where as sophisticated, the set of instructions are kept simple (especially so for [RISC](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer)). It's like teaching someone how to cook for the first time; the person has no concept of how to mix ingredients or control heat, so instead we give easy directions like "add in 1 gram of salt" and "let it simmer for 7 minutes" and "no no don't touch the fire!"

Let's continue the cooking analogy for a bit. Say you're preparing a meal; you have all your ingredients laid out, but you only have one cutting board and one stove. Moreover, you're working alone and can only do one thing at a time. With each task, you're completing one **instruction**.

One of your dishes combines a meat with a vegetable, so you have to cook them separately before putting them together. But you only have one stove! You work around this by cooking the meat first, then setting it aside to make space for cooking the vegetable. A computer might call this **memory management**. Being the experienced cook you are, you can make decisions on the fly like changing the recipe order or lowering the heat. In doing so, you're defining the **control flow**. 

With that, we now have an intuition for how a basic assembly program does its core tasks on the processor. Delicious.

{% include image.html url="/assets/img/cook.jpg" %}

This is the first thing I find amazing; at a low level, everything computers do seem so intuitive and so mundane. Yet, these simple machine instructions can be combined in so many ways to create every program in existence. A Chinese idiom sums it up well: “麻雀虽小，五脏俱全” (a tiny sparrow still has every organ it needs).


### The Complexity of Computers

However, it would be a massive understatement to call modern software "a bunch of instructions." Learning an assembly language has shown me that even in basic programs, there's so much going on under the hood, all thanks to **abstraction**. 

Here's a Python program that seems almost childish at first glance. 

```python
s = 'Hello world!'
print(s)
```

But what goes on inside (assuming [CPython](https://en.wikipedia.org/wiki/CPython))?
- A compiler breaks down the code into pieces ([bytecode](https://en.wikipedia.org/wiki/Intermediate_representation)) that are easier for machines to digest
- Another program called the interpreter executes this bytecode at runtime
- The string object labeled `s` is interally converted to a bunch of simpler data types
- Different data types have different standards for encoding information in bits
- Data is stored in memory so that the processor can act on it part by part
- Addresses keep track of where data is stored in memory
- Concepts like the stack and the heap keep data and addresses organized
- The `print` function has instructions for sending data to the OS output stream
- The OS takes care of displaying the data in the right place
- At the end, the program tells the OS it's done using memory

Even in this handwavy overview of a simple example, so many components need to work together without error. All just for a text back! Not every language implementation follows these steps, but generally speaking, the easier it is to write, the greater the iceberg effect. Also consider this: every step in this process requires some other program, such as the compiler or the OS, that's built on some form of abstraction itself. CPython is written in C, and C compiles down to assembly. Assembly instructions are abstractions of machine code, which are in turn abstractions of logic circuits. In professor Nikolic's words, **"It's all abstraction."** In my own words, "🤯."


### Built By Humans

Computers are fascinating both in their simplicity and in their complexity. However, this fascination may be misdirected, because humans are the ones who designed and built every computer, after all.

When I'm working with assembly, I feel like I have a flashlight to navigate the black box inside a computer, and I begin to notice many clues that seem to shout, "a human has been here!" I'm talking about how the processor is designed, how memory is structured, how data types are encoded, how procedures are optimized, and countless other details going into the implementation of a real computer. Within each detail, I can see all the human reasoning and considerations, and why the creator made it the way it is, and *it all makes so much sense*. As the cooking analogy from earlier hopefully demonstrates, the way a computer thinks isn't so different from the way a human thinks. I believe this sets computer science apart from many other branches of science, like physics. Whereas physics focuses on uncovering the laws of nature, computer science is about exploring a system created by us. 

In modern computing, the sheer amount of abstractions seems to hide away all these human details, but I think complexity is also a human trait in and of itself. This time, look at what computers and physics have in common: both disciplines are founded on a core set of principles, and humans build upon and evolve them to arrive at a massive yet interconnected model that fits our needs. In fact, the human penchant for complexity can be observed many disciplines outside of science too, like economics and politics. Every human endeavor becomes more complex as it progresses, and looking backwards, every system can be reduced to a few basic principles.

TL;DR: **Computer science is inseparable from humans.**

This is all very fancy and abstract, but here's my practical takeaway: **Don't be afraid to dig deep.** No matter how intimidating a subject may appear, it's created and studied by humans who think and reason similarly as you. Once you can grasp the few underlying concepts, all the complexity around it falls into order too.
