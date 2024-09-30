---
title : 'Session 1: Introduction to Machine Learning and AI safety'
date : 2024-04-02T01:00:47+07:00
draft : false  
---

## Goals and benefits of and what even is UAAR

1. Understanding AI, the problem of AI safety, and its importance
2. Make new friends
3. Network with people in the field
4. Funding/resources members are eligible to receive: including but not limited to books, compute resources for projects,  free drinks and snacks at meetings, etc.
5. Opportunities members are opened up to: research fellowships, part-time and full-time work opportunities, funding for projects and career development.
6. Making real, visible progress in AI safety & getting work experience (by participating in research sprints, other hackathon, doing self research, writing papers, and more)
7. And always remember to have fun :)

## ML background knowledge

We recapped a bit of the two 3B1B videos on [Neural Networks](https://youtu.be/aircAruvnKk) and [Gradient Descent](https://youtu.be/IHZwWFHWa-w).  
We established the following:

- Modern AIs are more like “matrices with a lot of numbers” than a software program
- We don’t so much code up AI, as we do find them, typically through gradient descent and backpropagation
- AI is quite good at doing things, despite this surprisingly “simple” concept of selection

![qronox writes on the whiteboard](/qronox_whiteboard_skrubz.png)

## Why is AI alignment a problem?

We discussed why us “finding” AI is unsettling, and why that leads to the alignment problem.

1) We don’t understand the AI at a low-level (the matrices are too big and complicated)
2) There is precedent for the AI not acting according to how we want it, both theoretical and empirical
3) This can become a massive issue for reliability, and further, when it can perform self-modification, an existential one too  
As of right now, there is no good solution to this problem.

## What are people trying to do to address this?

- Agent foundations  
*Mathematics for figuring out what an agent is or does*
- AI policy  
*Legal stuff for prevention of AI misuse and regulating AI development*
- Concept-based interpretability  
*What the AI is doing; in terms of high-level “features”, as opposed to circuits (mech-interp)*
- Mechanistic interpretability  
*What the AI is doing; in terms of its individual or groups of neurons*
- Red-teaming  
*Hacking the AI to force it to spit out misaligned output so we can identify and fix it*
- Cooperative AI  
*Improving human - AI or AI - AI cooperation.*
- Dangerous capabilities evaluation  
*Evaluate how dangerous the AI is, see if we can elicit dangerous capabilities from current models, create rigorous evaluations to ensure we can detect dangerous capabilities when they arise*
- Scalable oversight  
*Building AI systems that scale up and can also evaluate other AI when their capabilities surpass ours*
- Many more…

![working hard from session 1](/qronox_aprtm.jpg)
