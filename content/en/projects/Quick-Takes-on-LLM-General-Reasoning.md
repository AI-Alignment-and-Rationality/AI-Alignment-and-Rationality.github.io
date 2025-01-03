---
title : "Quick Takes on LLM General Reasoning"
date : 2025-01-03
toc: true
author: ["Jord Nguyen"]
draft : false
weight: 197
---

### Are LLMs general reasoners?
- Not just LLMs: You can substitute LLM for foundation models or general purpose transformers
- If you define "general reasoning" as "thinking carefully and generalising that thinking to any novel domains" then yes, 
I think current LLMs are definitely capable of it. 
- If you mean any novel domains that humans can generalise to, I lean to yes for more advanced LLMs. 
- If you mean generalisation to *literally everything ever*, then no, humans are not general reasoners either.

### Some evidence for LLM reasoning capabilities
- They have world models, representing concepts like space and time (https://arxiv.org/abs/2310.02207), 
modelling their data generating process (https://arxiv.org/abs/2405.15943), and modelling complex 
processes seem to transfer between different reasoning tasks (https://arxiv.org/abs/2410.02536)
- Very small transformers can be trained to grok algorithmic tasks / implicit reasoning tasks 
(https://arxiv.org/abs/2405.15071)
- Simplicity biases (https://arxiv.org/abs/2403.02241) making generalised approximations more likely than 
purely pattern matching
- Transformers are also Turing complete (https://arxiv.org/abs/2410.03170)
- They can learn in-context in a similar way to gradient descent (https://arxiv.org/abs/2212.07677)
- All the above + scaffolding (perhaps as simple as writing memory into a notepad) + most "models will never solve this 
reasoning problem/benchmark" being solved one generation later 

### Evidence against LLM reasoning capabilities
- Models fail at some simple OOD stuff (some interesting failures are at anti-riddles like "two pairs of father-son 
and 4 fish" instead of 3) (do check this out though https://arxiv.org/abs/2402.10200)
- Some examples of inverse scaling where small models answer normally and larger models mimic cliches / common misconceptions
- https://arxiv.org/abs/2405.15071 shows that small transformers can approximate algebraic structures 
such as composition but fail OOD, and they did some interp to figure why this was. 
- I would be surprised and update as such if straightforward modifications do not significantly increase performance on 
similar tasks. by straightforward im broadly gesturing at scaling / scaffolding / modular stuff like 
decoding / combinations of all above (Dec 2024 update: o3)
- I would also be convinced otherwise if someone demonstrates a theoretical limit on transformers’ 
(or anything you consider LLMs) OOD generalisation capabilities and ~1 decade worth of today’s ML field’s 
effort cannot make significant progress. I don’t think this would be practically useful though.

### More broadly
- My feeling is that LLMs are soup, a bundle of memorisation, shallow heuristics, and generalised circuits 
(probably related to shard theory or something)
- Evidences against don't seem to be fundamental problems that scaling or just improved training techniques won't bypass

### Why this matters
- (I think) there's a pretty good chance that LLMs + tools scale to transformative AI (more likely to automated 
R&D than/before AGI directly) (see RE-bench https://metr.org/blog/2024-11-22-evaluating-r-d-capabilities-of-llms/)
- This is probably relevant to safety risks and timelines, see https://www.lesswrong.com/posts/k38sJNLk7YbJA72ST/llm-generality-is-a-timeline-crux for a more comprehensive review

### What to do
- I’m doing a project at AI safety camp to gain more clarity on LLM automated RnD and general reasoning: 
https://forum.effectivealtruism.org/posts/2qJMDADRCPrkftRgb/ai-safety-camp-10#_8__LLMs__Can_They_Science_
    - There are lots of other interesting evals ideas to work on here:

        - How does tooling generally affect model performance(improvements, degradations from bad tooling)?
        - Can you make a super simple scaffolding scheme and get significant capability gains? 
        Simple memory summarisations + notepad, optimising prompts for successors, etc
        - Multi-agents? Large scale cooperation (on the order of millions of instances) have been found possible  

- Put more effort into developing tools / frameworks for effective evals/control/interp of advanced LLMs. 
There are lots of useful libraries for interp, evals has inspect, but lots of rooms left for building

