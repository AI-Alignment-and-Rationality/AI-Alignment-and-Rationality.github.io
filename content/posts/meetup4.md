---
title : 'Meetup4'
date : 2024-04-04T21:53:44+07:00
draft : false 
---

## Session 4: Intro to RHLF and Forecasting

### Intro to RLHF

- We watched [How a Coding Error Optimized GPT-2 for Bad Behaviour Instead of Good](https://youtu.be/qV_rOlHjvvs) as introductory material from Rational Animations about failure trying to do RLHF in OpenAI’s training of GPT2, due to a bug in its reward function.
- We went over the materials in Week 3 of BlueDot Impact’s AI Safety Fundamentals Course. In it, we discussed what RLHF is and some problems with the technique, both fundamental and tractable.

### A Walkthrough in Forecasting

- We watched [Introduction to Forecasting](https://www.youtube.com/playlist?list=PL4K6kMBfuK2kdCdIqTs40t7NsQfBCwPIC) by Dart Throwing Spider Monkey (great name) on the light theoretics, techniques, and applications of forecasting.
- We then tried applying these techniques on a toy problem: how likely is Jord to become a coauthor on the SATML paper? Each person was tasked with doing their own research to produce a probability. The following is each of our members’ methodologies:
  - Mogu’s “bogo” prediction: Randomly generate a number between 1 - 100 => 9%
  - TheBlindMeister’s prediction: Methodology unclear => 20%
  - purplechair’s “relevant search” prediction: Took the number of stars on the GitHub repo as number of participants, did the evaluations himself, got his success rate, converted it to Jord’s using the JP coefficient => 30.12%
  - Gumperto’s “improved bogo” prediction: Knew the distribution of problem difficulty is not uniform so took 50/50, where 2/4 trojans are easy so 10% each, the other two are harder are harder so ~15% each => 49% (the relevant information of Jord being worse than other participants reduced this down 1%)
  - Qronox  “peer pressure” prediction: Did his own research, gave up, and then took purplechair’s word for it => 30%

For an extra challenge, we also tried to calculate the amount of money we expected Jord to receive by the end of the competition

### More resources added 