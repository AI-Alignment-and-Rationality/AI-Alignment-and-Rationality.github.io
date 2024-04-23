---
title : 'Session 1: Introduction to Machine Learning and AI safety'
date : 2024-04-02T01:00:47+07:00
draft : false  
cover:
    image: /bible-cn_mozart-2x.png
---

We recapped a bit of the two 3B1B vids on Neural Networks and Gradient Descent. Also went into some more detail about some different activation functions (nothing too in detail just their general shape essentially)  

After we established that an AI is basically the matrix of weights (could include the process of finding the elements of that matrix itself depending on what you think an AI is) we began talking about AI safety  

### Basic argument for AI alignment

We don't know exactly what numbers in matrix do or mean:

- We don't know if the AI's solution matches our intuition for real world problems
Example: pausing in Tetris to make game length arbitrarily large instead of actually playing the game well
- A very intelligent AI may be able to come up with more sophisticated means of cheesing the system
- No reason why it shouldn't cheese the system (it only wants to do its "job" well)
- Could be a disaster in many ways

Some notes as to why:

- An intelligence may reason that to do its job it needs to first exist
- Its job specification may or may not include things that may or may not be important to humans
- It may misunderstand this specification
- This important thing could be lost or damaged
- And many more (this will be discussed in further depth in later sessions)

What are people trying to do to address this?

- Interpretability (what is the AI doing)
- Evaluation (how dangerous is the AI)
- …
