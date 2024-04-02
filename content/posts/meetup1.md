---
title : 'Meetup1'
date : 2024-04-02T01:00:47+07:00
draft : false  
cover:
#   image: https://i.kym-cdn.com/entries/icons/facebook/000/048/743/right_ear_left_ear.jpg
    image: ../assets/bible-cn_mozart-2x.png
---

# Session 1: Introduction to Machine Learning and AI safety

Location: Qronox’s apartment  
## Attendance:
- Jord (Executive + facilitation)
- Purplechair (Financial + facilitation)
- Gumperto
- Mogu 
- Qronox
- Skrubz
- TheBlindMeister
- Sparky

![horse.jpg](../assets/horse.jpg "he watches")

## Goals and benefits of and what even is UAAR
1. Understanding AI and AI safety
2. Make new friends
3. Network with people in the field
4. Funding/resources members are eligible to receive: including but not limited to bus ticket refunds, borrowed books, free courses, etc.
5. Opportunities members are opened up to: research fellowships, part-time and full-time work opportunities, etc.
6. Making real, visible progress in AI safety & getting work experience (by participating in hackathons, research sprints, and other competitions, writing papers, and more)
7. And always remember to have fun :)

## ML background knowledge
We recapped a bit of the two 3B1B videos on Neural Networks and Gradient Descent.

### We established the following:
- An AI is basically the matrix of weights (could include the process of finding the elements of that matrix itself depending on what you think an AI is)
- Upon multiplication with an input vector (and subtraction of another bias vector), we get a new vector, which would either continue to be fed into the coming hidden layers to be further multiplied with more weights, or be spat out as an output (if it’s the last layer)
- Gradient Descent is the process of using multivariable calculus to find a function that best predicts the dataset we fed the AI as well as future data it might find (much like plotting a best-fit line in Stats). It calculates the gradient vector (direction of steepest ascent) of its current loss function, and moves opposite of that, to the direction of steepest descent. When it finds a local minimum, it settles there, and the matrix of weights that correspond to the loss value at that point is the AI we end up with.
=> If this dataset is a good enough approximation of the real world, the AI can be very capable
Why is AI alignment a problem?
But then what’s so scary about numbers in a matrix? Something that should be rather unsettling about AI is that we don't know exactly what the numbers in its incomprehensibly massive matrix do or mean. If this isn’t obvious why yet, recall two of the following facts from Computer Programming and Calculus:
An optimal solution to a problem may not be immediately obvious (meaning it is surrounded by bad solutions), and an immediately obvious solution may not be optimal
Since the loss function can look like any numbers of the functions we’re already familiar with in Calculus, it may (and usually it does) have more than just one local minimum. These local minimums may or may not have the same loss value, but the important thing is the weights in the matrix are different every time, and this may result in wildly different behaviors, outside of the training data.
This has many uncomfortable implications on the reliability, and further the safety of AI: we don't know if the AI's solution matches our intuition for real world problems. For algorithmic problems, maybe it’s good that it doesn’t. For problems which we might have something we value other than isolated algorithmic efficiency, namely morality, reliability, comprehensibility, etc, not so much.

An example of this is the Tetris-playing AI pausing in Tetris when it’s about to lose, to make game length arbitrarily large so it doesn’t lose any points (minimizing loss), instead of choosing to lose the game, which does net it negative points (increasing loss). 
 
This is an example of an AI that’s still rather rudimentary, but even with simple AI, it should already raise concerns for the reliability of systems if they could just simply do things like this without any warning. But okay, let’s be cooler heads here. A skeptic could argue that “Yes, this is ominous, but a truly hyperintelligent system would be able to find a way to win the game, regardless of the game state. Surely, if we keep developing better AI systems, the problem will just solve itself.” This is probably true, and perhaps for AGI, Tetris may well be the most exciting frontier.

And why shouldn’t it be? If there were a way to win the game, then that proves the coward’s way out of pausing the game is suboptimal, indicating the Gradient Descent process had landed on a local minimum, not the function’s true minimum. This, in turn, implies that an AGI system, which is able to model itself as part of its own data, much like how we can model ourselves in the real world, should thus be able to modify itself to always land on the true minimum, and never have to resort to indefinite pausing again! Alignment solved!

But therein lies the problem. This would only mean the AI is extraordinarily amazing at completing Tetris, and it doesn’t really care about the pause button, or anything else really.  Translated to real-world-problem terms, the AI is very proficient at finding the most optimal solution, but since it happens that morality and other such yucky human values are quite suboptimal (real life pause buttons, to some degree), and the AI, being perfectly able to model that, perfectly knowing that humans coded those values into it to stop it from reaching a true minimum that we don’t want, can simply just “write” those values out of the local minimum, into a true one. A very intelligent AI opens up vastly many more dimensions we can scarcely even comprehend for “cheesing the system”.

### As of right now, there is no good solution to this problem.
What are people trying to do to address this?
- Agent foundations 
Mathematics for figuring out what an agent is or does
- AI governance, policy 
Legal stuff for prevention of AI misuse
- Concept-based interpretability 
What the AI is doing; in terms of its general structure
- Mechanistic interpretability 
What the AI is doing; in terms of its individual weights
- Control, Red-teaming 
Hacking the AI to force it to spit out misaligned output so we can identify and fix it
- Cooperative AI
Improving human - AI cooperation
- Dangerous capability evaluation 
Evaluate how dangerous the AI is
- Scalable oversight 
Building systems that scale and can also evaluate AI
- Many more…
