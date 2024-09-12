---
title : ' Session 4: Intro to RHLF and Forecasting'
date : 2024-04-04T21:53:44+07:00
draft : false 
---

## Intro to RLHF

- We watched [this video](https://youtu.be/qV_rOlHjvvs) as introductory material from Rational Animations about failure trying to do RLHF in OpenAI’s training of GPT2, due to a bug in its reward function.
- We went over the materials in Week 3 of BlueDot Impact’s AI Safety Fundamentals Course. In it, we discussed what RLHF is and some problems with the technique, both fundamental and tractable.

## A Walkthrough in Forecasting

**Motivation**: AI Safety is concerned with a breakdown of society due to A(G)I, but as of 17/3/2024, neither instances of these have ever happened in human history. We have a useful qualitative tool for anticipating them, called imagination, but to somewhat quantify them, we use something called forecasting.

- We watched [this video series](https://www.youtube.com/playlist?list=PL4K6kMBfuK2kdCdIqTs40t7NsQfBCwPIC) by Dart Throwing Spider Monkey (great name) on the light theoretics, techniques, and applications of forecasting.
- We then tried applying these techniques on a toy problem: how likely is Jord to become a coauthor on the CNN Interpretability SATML competition report paper? Each person was tasked with doing their own research to produce a probability. The following is each of our members’ methodologies:

Jord’s sample prediction: ![jord's prediction](/jord_prediction.jpg)

Took the mean of the success rates for his particular method on natural feature trojans => 59%

Some predictions:
| member | reason | prediction |
|:---:|:---:|:---:|
|purplechair| “relevant search” prediction: Took the number of stars on the GitHub repo as number of participants, did the evaluations himself, got his success rate, converted it to Jord’s using the JP coefficient | 30.12% |
|TheBlindMeister|Read up on undergraduate coauthor publishing rates|20%|
|Gumperto|“improved bogo” prediction: Knew the distribution of problem difficulty is not uniform so took 50/50, where 2/4 trojans are easy so 10% each, the other two are harder are harder so ~15% each|49% (the relevant information of Jord being worse than other participants reduced this down 1%)|

For an extra challenge, we also tried to calculate the amount of money we expected Jord to receive by the end of the competition. Below are purplechair’s and Gumperto’s calculations:

purplechair's prediction: ![purplechair's prediction](/image14.jpg)
gumperto's prediction: ![gumperto's prediction](/image9.jpg)

**Update**: Jord did end up getting coauthor in the SATML report paper (closest prediction was Jord’s), and he received a total of 200$ from it (closest prediction was purplechair’s).

## Resources update

- Jord went and introduced to everyone a few new resources and opportunities at the end of the session  

Jord’s forecasting resolution note: Since this was an AI conference competition report paper, choosing a base rate of undergraduate coauthors from psychology research journals (the only source we found) was highly inaccurate.
