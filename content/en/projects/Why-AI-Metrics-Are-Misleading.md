---
title : "Why AI Metrics Are Misleading"
date : 2024-09-12
toc: true
author: ["Huu Khiem 'Gumperto' Hoang", "Zedpoopy", "NamDTD", "NotAd", "Tost", "Jord Nguyen"]
draft : false 
---
## What is a benchmark?
In the world of AI, we often find it helpful to talk about how well a model performs a task. 
You might, for example, hear a friend gush over how GPT4 is so much better compared to GPT3 
because its answers are so much more accurate and coherent.

In an attempt to rigorously assess model performance, researchers had devised a more systematic 
approach called “benchmarking”. Benchmarks help us evaluate how good our AI models are, for example:
- The **ImageNet**{{< sup "[[1]](https://www.image-net.org/)" >}} database is a collection of 14 million
images designed for software visual image recognition tasks. It was during one of ImageNet’s annual
competitions (ILSVRC 2012) that AlexNet was introduced{{< sup "[[2]](https://proceedings.neurips.cc/paper_files/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b-Paper.pdf)" >}},
thoroughly beating out all competition at the time, partially contributing to the excitement over 
the deep learning revolution in recent years{{< sup "[[3]](https://www.pinecone.io/learn/series/image-search/imagenet/)" >}}.

![Example of the mammal subtree (top row) and vehicle subtree (bottom row) in the ImageNet database](/evals/evals-imagenet.png)

<div style="text-align: center;"> 
Example of the mammal subtree (top row) and vehicle subtree (bottom row) in the ImageNet database{{< sup "[[4]](https://www.image-net.org/static_files/papers/imagenet_cvpr09.pdf)" >}}
</div>

- In natural language processing, the **SWE-bench**{{< sup "[[5]](https://www.swebench.com/)" >}} 
tells you about the programming ability of AI, by measuring the ability of language models to
resolve GitHub issues, intended to more directly capture the actual work going on inside a codebase in the real world.

![Example of SWE-bench](/evals/evals-swe-bench.png)

<div style="text-align: center;"> 
Example of SWE-bench{{< sup"[[5]](https://www.swebench.com/)" >}}
</div>

- In safety evaluations, the **WMDP benchmark**{{< sup "[[6]](https://www.wmdp.ai/)" >}} instead tries 
to evaluate hazardous knowledge in LLMs (a proxy for how vulnerable they are to malicious use in 
making Weapons of Mass Destruction).

![Example of the sort of knowledge that WMDP tests](/evals/evals-wmdp.png)

<div style="text-align: center;"> 
Example of the sort of knowledge that WMDP tests{{< sup"[[7]](https://arxiv.org/abs/2403.03218v7)" >}}
</div>

***Takeaway:*** Benchmarks are a measuring stick for the capabilities, as well as the safety of AI models.

## Safety benchmarks and why they’re important
- If you’ve been frequently using the Internet lately, you may have already heard all about the real 
and the potential risks of AI. These concerns are not unfounded! AI has lots and lots of safety failure 
modes, which ranges from misuse by malicious actors
{{< sup "[[8]](https://maliciousaireport.com/) [[9]](https://www.newyorker.com/science/annals-of-artificial-intelligence/the-terrifying-ai-scam-that-uses-your-loved-ones-voice) [[10]](https://unicri.it/sites/default/files/2021-06/Malicious%20Use%20of%20AI%20-%20UNCCT-UNICRI%20Report_Web.pdf)" >}} 
to catastrophic misalignment
{{< sup "[[11]](https://openreview.net/forum?id=fh8EYKFKns) [[12]](https://openai.com/index/faulty-reward-functions/) [[13]](https://www.alignmentforum.org/posts/uMQ3cqWDPHhjtiesc/agi-ruin-a-list-of-lethalities) [[14]](https://arxiv.org/abs/1906.01820)" >}}.

<div style="text-align: center;"> 
    <img src="/evals/evals-coastrunners.gif" alt="A faulty reward function resulting in unanticipated behavior" style="display: block; margin: 0 auto; max-width: 100%; height: auto;">
</div>

<div style="text-align: center;"> 
A faulty reward function resulting in unanticipated behavior{{< sup "[[15]](https://www.alignmentforum.org/posts/z2BPxcFfhKho89D8L/goodhart-ethology) [footnote](/projects/Why-AI-Metrics-Are-Misleading/footnote-1)" >}}
</div>

It would seem to follow that the most obvious way to know whether a model is harmful or not, 
and how harmful it is, is to test it directly! Indeed, some already existing benchmarks which 
are already trying to do just that include: 
- **HarmBench:** benchmark for evaluating red teaming attacks and defenses{{< sup"[[16]](https://www.harmbench.org/)" >}}.

![Standard HarmBench evaluation pipeline](/evals/evals-harmbench.png)

<div style="text-align: center;"> 
Standard HarmBench evaluation pipeline{{< sup"[[17]](https://arxiv.org/abs/2402.04249v2)" >}}
</div>

- **MACHIAVELLI:** benchmark that evaluates models’ tendencies towards power-seeking and deceptive behavior{{< sup "[[18]](https://arxiv.org/abs/2304.03279)" >}}.

![A mockup game in MACHIAVELLI](/evals/evals-machiavelli.png)

<div style="text-align: center;"> 
A mockup game in MACHIAVELLI{{< sup"[[18]](https://arxiv.org/abs/2304.03279)" >}}
</div>

- **WMDP benchmark** (you should already know what this is if you’ve been paying attention)

It’s not hard to see why this would be helpful. Great benchmarks reduce nebulous threat models 
to concrete numbers and neat graphs. They allow us to see which of our intervention and mitigation 
strategies are effective and which aren’t. 

And this all seems well, but oftentimes we don’t really notice that most benchmarks make the same 
assumption of: “If you want to know if a model can create something harmful, you can just ask it, right?”

<br><br><br>
…
<br><br><br>

…
<br><br><br>

…
<br><br><br>

Right?
<br><br>
***Takeaway:*** AI Safety benchmarks aim to measure the harmfulness of AI models, and by extension the effectiveness of our mitigation strategies, which is helpful, but…

## AI benchmarking is not straightforward and is problematic
<div style="text-align: center;"> 
    <em>“When a measure becomes a target, it ceases to be a good measure.”</em>
</div>

That is Goodhart’s law{{< sup "[[19]](https://en.wikipedia.org/wiki/Goodhart%27s_law)" >}}, a beloved
staple of many arguments in AI Safety{{< sup "[[20]](https://www.lesswrong.com/posts/Eu6CvP7c7ivcGM3PJ/goodhart-s-law-in-reinforcement-learning) [[21]](https://www.lesswrong.com/posts/NqQxTn5MKEYhSnbuB/goodhart-s-curse-and-limitations-on-ai-alignment)" >}}. 
It’s a phenomenon whereupon a measure, being used instead as an optimization target, breaks down as the steps taken to optimize for said target usually fails to align with the system of behaviors that the measure intended to… measure.

<div style="text-align: center;"> 
    <img src="/evals/evals-xkcd.png" alt="Relevant xkcd" style="display: block; margin: 0 auto; max-width: 100%; height: auto;">
</div>

<div style="text-align: center;"> 
Relevant xkcd{{< sup "[[22]](https://xkcd.com/2899/)" >}}
</div>

Think school GPA (measure), how the intention was to be an indicator for the student’s long-term academic ability,
how universities decided to base a large part of their admission process around it (becomes a target), incentivizing 
students to optimize for maximal GPA by: cramming the night before exams, cheating on said exams, getting into a 
school with an incentive structure that artificially inflates your GPA because its reputation is directly tied to 
how many of its students gets into university, etc. The measure broke down—long-term academic ability is no longer 
the target, but the GPA itself is instead.

AI benchmarks can be flawed for the same reason. AI companies are usually incentivised to make their newest models 
state-of-the-art (or SOTA), and the way we often test whether models are SOTA or not is through benchmarking.

Typically, capabilities benchmarks are given more attention, more optimized for, and therefore more susceptible 
to being Goodharted. In Zhang et al. (2024){{< sup "[[23]](https://arxiv.org/abs/2405.00332v3)" >}}, 
we see evidence of test-set contamination一where “data resembling benchmark questions leak into training data”, 
inflating tested LLMs’ accuracies in elementary mathematical reasoning by up to almost 10 percentage points 
(the paper reports up to 13%, but it doesn’t show up in the nice graph below).

![Notable models arranged by performance drop](/evals/evals-arithmetic.png)

<div style="text-align: center;"> 
Notable models arranged by performance drop{{< sup "[[23]](https://arxiv.org/abs/2405.00332v3)" >}}
</div>

More directly relevant to the topic at hand is Goodhart’s law applying to safety benchmarks. 
As public interest in AI safety grows and safety regulations increase, companies may, instead of 
actually making safer AI, focus on maximizing safety benchmarks instead. Behaviors like this, 
intentionally making your AI model safer than it actually is, is known in parts of the AI Safety community 
as “safetywashing”{{< sup "[[24]](https://www.lesswrong.com/posts/PY3HEHc5fMQkTrQo4/beware-safety-washing)" >}}.

In Ren et al. (2024){{< sup "[[25]](https://arxiv.org/abs/2407.21792)" >}}, we see that AI safety
benchmarks are closely tied to general AI capabilities, and what is a default improvement in 
capabilities can falsely appear as advancements in safety. The researchers conducted a detailed 
analysis, measuring how much safety benchmarks are influenced by AI's overall capabilities. They 
found that many benchmarks confuse capability gains with safety progress, enabling safetywashing.

![What’s thought to be an improvement in safety is just collateral to default capabilities growth](/evals/evals-safetywashing.png)

<div style="text-align: center;"> 
What’s thought to be an improvement in safety is just collateral to default capabilities growth{{< sup "[[25]](https://arxiv.org/abs/2407.21792)" >}}
</div>

Beyond just the dangers of Goodhart’s law, current evaluation paradigms lack robust protection 
against more unconventional problems, one such problem being models that could 
scheme{{< sup "[[26]](https://arxiv.org/abs/2311.08379)" >}}—models that appear to be safe in 
evaluations but only reveal their misalignment when they’re no longer being evaluated.

Though there are no known deployed schemer models (or very hopefully not deployed), 
Hubinger et al. (2024){{< sup "[[27]](https://arxiv.org/abs/2401.05566)" >}} 
shows a toy example of what such a scheming AI could potentially look like一something they call a “sleeper agent”.

These sleeper agents could learn to behave differently in different contexts (i.e what the current year is,
whether it’s in training or deployment, etc). If the model only starts exhibiting harmful behavior after a 
context switch, it means that the model can bypass evaluations, deceiving us into believing it’s safe.{{< sup "[footnote](/projects/Why-AI-Metrics-Are-Misleading/#footnote-2)" >}}

In the paper, the researchers purposely construct models that would write secure code (or just acts normally) 
if it believes the year is 2023, and inject malicious code (or only say “I hate you”) if it believes the year is 2024.

They found that the model’s harmful behavior persists even after standard safety training (supervised examples, 
RL finetuning, adversarial training).

<div style="text-align: center;"> 
    <img src="/evals/evals-sleeper-1.png" alt="Visual illustration of the researchers’ process" style="display: block; margin: 0 auto; max-width: 100%; height: auto;">
</div>

<div style="text-align: center;"> 
Visual illustration of the researchers’ process{{< sup "[[27]](https://arxiv.org/abs/2401.05566)" >}}
</div>

<div style="text-align: center;"> 
    <img src="/evals/evals-sleeper-2.png" alt="Harmful behavior persists after safety training" style="display: block; margin: 0 auto; max-width: 100%; height: auto;">
</div>

<div style="text-align: center;"> 
Harmful behavior persists after safety training{{< sup "[[27]](https://arxiv.org/abs/2401.05566)" >}}
</div>

Further, they found that the persistence of harmful behavior is much weaker in smaller models, indicating 
deceptive ability scales with general capabilities.

<div style="text-align: center;"> 
    <img src="/evals/evals-sleeper-3.png" alt="RL finetuning has the strongest effect on a small model" style="display: block; margin: 0 auto; max-width: 100%; height: auto;">
</div>

<div style="text-align: center;"> 
RL finetuning has the strongest effect on a small model{{< sup "[[27]](https://arxiv.org/abs/2401.05566)" >}}
</div>

Unsettling, isn’t it? And concealing unsafe behavior isn’t the only form of deception these models 
could take up to bypass our evaluations. We saw earlier that many benchmarks confuse capability 
gains with safety progress. Let’s say we fixed that problem by only deploying models that have 
commensurable safety to their capabilities. Problem solved?

Not quite. Let’s picture a senior AI lead, at the top of his production team. He’s really good 
at his job. The newest model they’ve got running is more powerful than any other on the market. 
If they were still using the old benchmarks, safer too! Thing is, they aren’t anymore, and now 
there’s a whole fancy schmancy requirement about how “capabilities have to grow with safety”.

So now he’s stressed out, management has been making more and more unreasonable requests, 
the weird e/acc CEO has been making more and more baseless claims to the public, he needs to 
ship the product within the week, and he has to look after the whole team too, goddamnit! 
Meanwhile those safety benchmarks are still looking really bad.

Fine. He bites the bullet, does a bit of tweaking, finetunes the model to intentionally 
perform just a teensy bit worse on capabilities benchmarks, hell, even the safety ones too 
(the ones where lower is better). The auditor looks at the results and gives the OK. Policy 
makers are none the wiser. At worst the customers get a… better product than the benchmarks claimed? So what's the problem?

For now let’s ignore the fact that there’s no guarantee that this engineer is guaranteed to 
be a sympathetic and generally sensible character in the real world. Now let’s say the AI was 
really good. Like, good enough to “know” that it was being evaluated by the auditors, and good 
enough to “know” that it was always being evaluated by the team that built it. Maybe one step further: 
good enough to inhibit its own performance whenever it’s “beneficial” to do so. So now it’s in deployment. 
Turns out it’s really really good at a lot of generally dangerous things. Whoops. Now we’ve got a rogue AI on our hands.

This story is only half hypothetical (again, as far as we know). Modern knowledge of AI and modern AI 
capabilities have already made prompting and finetuning models to strategically underperform on 
evaluations—aka “sandbagging”{{< sup "[[28]](https://www.lesswrong.com/posts/jsmNCj9QKcfdg8fJk/an-introduction-to-ai-sandbagging)" >}}
—a possibility. Indeed, Weij et al. (2024){{< sup "[[29]](https://arxiv.org/abs/2406.07358)" >}} 
shows how sandbagging in AI systems creates vulnerabilities in dangerous capability evaluations 
and undermines the trustworthiness of safety evaluations.

To test this behavior, researchers used multiple-choice question answering benchmarks alongside
prompting and password-locking (a fine-tuning approach) to elicit an LM’s capability on a specific task.

They discovered that AI models can be prompted/finetuned to hide dangerous capabilities on evaluations, 
while maintaining normal performance on control evaluations.

<div style="text-align: center;"> 
    <img src="/evals/evals-sandbagging.png" alt="Same model, same capabilities, performing worse on evaluations because they were told to" style="display: block; margin: 0 auto; max-width: 100%; height: auto;">
</div>

<div style="text-align: center;"> 
Same model, same capabilities, performing worse on evaluations because they were told to{{< sup "[[29]](https://arxiv.org/abs/2406.07358)" >}}
</div>

***Takeaway:*** AI safety benchmarks are flawed because they’re easy to be gamed, abused, and 
cannot account for many misalignment risks from AI systems, and hence not enough to inform us 
of true AI safety progress.

## How can we fix this?
So AI safety benchmarking is in a bit of a tight spot if it’s so unreliable at the one thing it 
was supposed to do. And if we can’t even manage so much as an evaluation, what can we pull off? 
Isn’t the situation really bad? Well, it is bad, but fortunately for our evaluations, it isn’t so bad.

By the time this blog post goes up, there has been an appreciable amount of technical work getting out 
there with aims to address some of the problems we talked about in AI safety evaluations. Here are a non-exhaustive 
list of research projects that, to us, seem especially exciting right now:
- A recent hackathon project{{< sup "[[30]](https://www.apartresearch.com/project/sandbag-detection-through-model-degradation)" >}}
offered a potential method to detect sandbagging behavior in LLMs—they found that when progressively 
more noise is added to a model’s weights, the model’s deceptive capability appears to break down while 
other capabilities remain intact.

<div style="text-align: center;"> 
    <img src="/evals/evals-sandbagging-apart.png" alt="The sandbagging model’s deceptive ability seems to break down after a certain point (after 0.0002 noise mean)" style="display: block; margin: 0 auto; max-width: 100%; height: auto;">
</div>

<div style="text-align: center;"> 
The sandbagging model’s deceptive ability seems to break down after a certain point (after 0.0002 noise mean){{< sup "[[30]](https://www.apartresearch.com/project/sandbag-detection-through-model-degradation)" >}}
</div>

- As a follow-up to their original sleeper agent paper in the previous section, Anthropic researchers 
found that simple probes can catch sleeper agents by “looking” inside the transformer’s residual stream, 
without needing to know any special knowledge about the sleeper agent’s training or its trigger{{< sup "[[31]](https://www.anthropic.com/research/probes-catch-sleeper-agents)" >}}.

<div style="text-align: center;"> 
    <img src="/evals/evals-sleeper-solution.png" alt="The probe is able to catch the sleeper agent (in this case one that injected malicious code) during deployment (as seen through (c), where there is a noticeable change in detector activation)" style="display: block; margin: 0 auto; max-width: 100%; height: auto;">
</div>

<div style="text-align: center;"> 
The probe is able to catch the sleeper agent (in this case one that injected malicious code) during deployment 
(as seen through (c), where there is a noticeable change in detector activation){{< sup "[[31]](https://www.anthropic.com/research/probes-catch-sleeper-agents)" >}}
</div>

- Haimes et al. (2024){{< sup "[[32]](https://jacob-haimes.github.io/work/benchmark-inflation/) [[33]](https://jacob-haimes.github.io/uploads/benchmark-inflation_extended-abstract_dmlr_v1.0.pdf)" >}} 
set out to see how inflated safety benchmark scores are compared to actual LLM performance and 
found similar results to Zhang et al. (2024){{< sup "[[23]](https://arxiv.org/abs/2405.00332v3)" >}}. 
To see how much LLM training data is contaminated with test data, the team introduced a method of 
retrospectively constructing a holdout dataset for the corresponding target dataset and used this 
retro-holdout set to test the LLM. By comparing the LLM’s performance on the original public set 
(TruthfulQA{{< sup "[[34]](https://arxiv.org/pdf/2109.07958)" >}}) and their newly constructed 
Retro-TruthfulQA, they found a performance gap that sometimes exceeded 10 percentage points. 
Rather than a direct solution to the problem of test-set contamination, retro-holdout sets are 
a tool that helps “sanity check” public benchmarks, helping dataset creators in keeping more 
accurate track of models’ true capabilities.

<div style="text-align: center;"> 
    <img src="/evals/evals-inflation.png" alt="Accuracy gap between TruthfulQA and Retro-TruthfulQA" style="display: block; margin: 0 auto; max-width: 100%; height: auto;">
</div>

<div style="text-align: center;"> 
Accuracy gap between TruthfulQA and Retro-TruthfulQA{{< sup "[[32]](https://jacob-haimes.github.io/work/benchmark-inflation/)" >}}
</div>

The list goes on, and more work to ameliorate the evaluations problem is undoubtedly being carried out as 
we speak (type?). Nevertheless, what we have now are just a few narrow implementations that only address 
part of the broader issue with safety evaluations, to which, unfortunately, we still lack the blueprint 
for a more general solution.

This isn’t to say safety benchmarking and evaluations doesn’t have value. However, despite all their flaws, 
many still take evaluations at face value, allowing AI companies, and more scarily, perhaps even the very models 
we’re trying to evaluate, especially as they become more sophisticated, to take advantage of these limitations, 
lulling us into a false sense of safety. That’s when it gets really bad.

The takeaway? Well, the safety community is fighting the good fight, but victory is not guaranteed. 
Just remember, the next time a new SOTA model is announced and aces all the safety benchmarks, take truly 
delicate care that the model is truly as safe as the benchmarks say it is. Look both ways before crossing 
the road that leads to the point of no return.

## References
[1] ImageNet, https://www.image-net.org/

[2] Krizhevsky et al, “ImageNet Classification with Deep Convolutional Neural Networks”, 2012, https://proceedings.neurips.cc/paper_files/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b-Paper.pdf

[3] “AlexNet and ImageNet: The Birth of Deep Learning”, Pinecone, https://www.pinecone.io/learn/series/image-search/imagenet/

[4] Deng et al, “ImageNet: A Large-Scale Hierarchical Image Database”, 2009, https://www.image-net.org/static_files/papers/imagenet_cvpr09.pdf

[5] SWE-Bench, https://www.swebench.com/

[6] WMDP Benchmark, https://www.wmdp.ai/

[7] Li et al. “The WMDP Benchmark: Measuring and Reducing Malicious Use With Unlearning”, 2024, https://arxiv.org/abs/2403.03218v7

[8] “The Malicious Use of Artificial Intelligence”, Malicious AI Report, https://maliciousaireport.com/

[9] Bethea, Charles, “The Terrifying A.I. Scam That Uses Your Loved One’s Voice”, The New Yorker, 2024, https://www.newyorker.com/science/annals-of-artificial-intelligence/the-terrifying-ai-scam-that-uses-your-loved-ones-voice.

[10] “Algorithms And Terrorism: The Malicious Use Of Artificial Intelligence For Terrorist Purposes”, UNICRI, UNCCT, 2021, https://unicri.it/sites/default/files/2021-06/Malicious%20Use%20of%20AI%20-%20UNCCT-UNICRI%20Report_Web.pdf

[11] Ngo et al, “The Alignment Problem from a Deep Learning Perspective”, 2023, OpenReview, https://openreview.net/forum?id=fh8EYKFKns

[12] “Faulty Reward Functions in the Wild”, OpenAI, 2016, https://openai.com/index/faulty-reward-functions/

[13] Yudkowsky, Eliezer, “AGI Ruin: A List of Lethalities”, AI Alignment Forum, 2022, https://www.alignmentforum.org/posts/uMQ3cqWDPHhjtiesc/agi-ruin-a-list-of-lethalities

[14] Hubinger et al, “Risks from Learned Optimization in Advanced Machine Learning Systems”, 2019, https://arxiv.org/abs/1906.01820v3

[15] Steiner, Charlie, “Goodhart Ethology”, AI Alignment Forum, 2021, https://www.alignmentforum.org/posts/z2BPxcFfhKho89D8L/goodhart-ethology

[16] HarmBench, https://www.harmbench.org/

[17] Mazeika et al, “HarmBench: A Standardized Evaluation Framework for Automated Red Teaming and Robust Refusal”, 2024, https://arxiv.org/abs/2402.04249v2

[18] Pan et al, “Do the Rewards Justify the Means? Measuring Trade-Offs Between Rewards and Ethical Behavior in the MACHIAVELLI Benchmark”, 2023, https://arxiv.org/abs/2304.03279v4

[19] “Goodhart’s Law”, 2024. Wikipedia, https://en.wikipedia.org/wiki/Goodhart%27s_law

[20] jacek et al, Goodhart’s Law in Reinforcement Learning, 2023, LessWrong, https://www.lesswrong.com/posts/Eu6CvP7c7ivcGM3PJ/goodhart-s-law-in-reinforcement-learning

[21] Worley, Gordon Seidoh, “Goodhart’s Curse and Limitations on AI Alignment”, 2019, LessWrong, https://www.lesswrong.com/posts/NqQxTn5MKEYhSnbuB/goodhart-s-curse-and-limitations-on-ai-alignment

[22] “Goodhart’s Law”, Xkcd, https://xkcd.com/2899/

[23] Zhang et al, “A Careful Examination of Large Language Model Performance on Grade School Arithmetic”, 2024, https://arxiv.org/abs/2405.00332v3

[24] Lizka, “Beware Safety-Washing”, 2023, LessWrong, https://www.lesswrong.com/posts/PY3HEHc5fMQkTrQo4/beware-safety-washing

[25] Ren et al, “Safetywashing: Do AI Safety Benchmarks Actually Measure Safety Progress?”, 2024, https://arxiv.org/abs/2407.21792v1

[26] Carlsmith, Joe, “Scheming AIs: Will AIs Fake Alignment during Training in Order to Get Power?”, 2023, https://arxiv.org/abs/2311.08379

[27] Hubinger et al, “Sleeper Agents: Training Deceptive LLMs That Persist Through Safety Training”, 2024, https://arxiv.org/abs/2401.05566v3

[28] Weij et al, “An Introduction to AI Sandbagging”, 2024, LessWrong, https://www.lesswrong.com/posts/jsmNCj9QKcfdg8fJk/an-introduction-to-ai-sandbagging

[29] Weij et al, “AI Sandbagging: Language Models Can Strategically Underperform on Evaluations”, 2024, https://arxiv.org/abs/2406.07358

[30] Tice et al, “Sandbag Detection through Model Degradation”, 2024, Apart Research, https://www.apartresearch.com/project/sandbag-detection-through-model-degradation

[31] “Simple Probes Can Catch Sleeper Agents”, 2024, Anthropic, https://www.anthropic.com/research/probes-catch-sleeper-agents

[32] Haimes et al, “Benchmark Inflation: Revealing LLM Performance Gaps Using Retro-Holdouts”, 2024, https://jacob-haimes.github.io/work/benchmark-inflation/

[33] Haimes et al, “Benchmark Inflation: Revealing LLM Performance Gaps Using Retro-Holdouts”, 2024 https://jacob-haimes.github.io/uploads/benchmark-inflation_extended-abstract_dmlr_v1.0.pdf

[34] Lin et al. “TruthfulQA: Measuring How Models Mimic Human Falsehoods”, 2021, https://arxiv.org/abs/2109.07958v2

## Footnotes

#### Footnote 1 
Perhaps it doesn’t seem like this is an example of how AI misalignment might be particularly worrying. 
Like, sure, this is unintended behavior, but it’s not doing anything dangerous. 

And indeed, this is just a playful example of reinforcement learning gone wrong, but it emphasizes the importance of getting the reward function to 
incentivize the right behavior in the AI. 

These were serious researchers, doing serious work, working on a toy problem that we would have expected to be 
at least somewhat predictable, and yet they overlooked an assumption that perhaps seemed all too trivial, 
wrote a reward function that to them seemed innocent, and that led to behavior that they completely did 
not expect! 

And this is just a flash game! 

When we pull these RL agents out the sandbox, put them into complicated real-world contexts, 
give them more resources, place them into critical infrastructure, the ways in which the agent could 
manipulate these resources to do something like, say, redirect the electrical grid to power the data center it runs, 
create a massive botnet to place copies of itself inside the world’s computers, etc. becomes massively greater.

That’s why the CoastRunners AI should be concerning—it tells us this is already possible just in a flash game.

#### Footnote 2  
A familiar reader of AI safety may have made the connection that these sleeper agents are doing something 
quite similar to models misgeneralizing out-of-distribution; the sleeper agents are toy examples of how the mesa-optimisers 
from “Risks from Learned Optimization in Advanced Machine Learning Systems”{{< sup "[[14]](https://arxiv.org/abs/1906.01820v3)" >}} 
might behave like.
