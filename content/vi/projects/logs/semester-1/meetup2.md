---
title : 'Session 2: Risks from Learnt Optimization'
date : 2024-04-04T21:26:41+07:00
draft : false 
---

![reading](/keepcafe1.jpg)
## Mesa-optimization and inner misalignment

- We read and discussed [this sequence / paper](https://www.alignmentforum.org/s/r9tYkB2a8Fp4DN8yB) live (3 hours)
- The really high-level gist of it was that:
  - In a machine learning setup, the gradient descent process (base optimizer) finds a model that does a task (base objective) well
  - Base optimizer finds in the sea of options and possibilities an algorithm (model) it “likes” and uses it to solve its problem. The model could be doing optimization itself. This would be called the mesa-optimizer.
  - A different objective (mesa-objective) is determined by the mesa-optimizer, not the base optimizer. This mesa-objective might be misaligned with the base-objective. Since the model could understand its optimization pressures, it might choose to deliberately hide its mesa-objective (deceptive alignment). In case of a distributional shift (environment changes), the model would pursue its mesa-objective instead.
  - The paper discusses some ways in which this could pose a problem to the alignment problem.

## How to break an AI model: [TensorTrust](https://tensortrust.ai/) (an LLM jailbreaking game)

- We tried out TensorTrust (0.5 hours)
- Introduced Purplechair, Mogu, Skrubz, and TheBlindMeister to some basic TensorTrust strategies and the format of a classical prompt injection attack.

![access granted?](/keepcafe2.jpg)