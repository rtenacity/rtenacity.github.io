---
layout: post
title: LLMs as Philosophical Zombies
date: 2025-09-10
description: Large Language Models (LLMs), the AI systems behind ChatGPT and similar tools, have reached new heights of popularity...
categories: philosophy artificial-intelligence
---


In my previous post, we introduced William James's pragmatic framework for free will, which requires three characteristics: chance, choice, and regret. Now, let's test whether Large Language Models actually demonstrate these qualities.

#### Chance

Due to the unpredictable, chance-based design of LLMs, these models are capable of being creative and spontaneous within patterns they've learned from human language. Unlike algorithms with predictable, fixed outputs, LLMs regularly produce outputs that surprise even their creators. LLMs are able to construct new combinations of concepts and reasoning patterns while never being tied to fixed outputs. In this sense, LLMs embody Jamesian 'chance': they create open possibilities that cannot be predicted in advance.

#### Choice

Reinforcement Learning from Human Feedback (RLHF) is a training method where humans rate AI responses to teach the system what kinds of answers are good, representing functional choice in LLMs. RLHF trains LLMs to consider options and select responses based on learned values. During this process, LLMs engage in something similar to deliberation. They consider multiple possible responses, compare them against their preferences and constraints, and select outputs based on value judgments. This is not a predictable process: the same LLM presented with the same prompt can produce different responses based on context and state variations. RLHF teaches LLMs to generalize value judgments to new situations, basically creating an internal 'code of values' for each LLM. This is why trained LLMs often turn down harmful or dangerous requests and are not incredibly racist or sexist (which they are by default, due to the bias of training materials). Essentially, we've replicated the ability of choice in an LLM.

#### Regret

Now, the final question we need to answer: can LLMs show regret and moral reasoning? At a first glance, we've seen that LLMs demonstrate 'intellectual humility', as they're able to reason and revise their initial ideas when presented with new evidence, acknowledging their shortcomings.

More rigorously, researchers from Microsoft tested seven major language models using the Defining Issues Test, a psychological test that presents moral dilemmas followed by twelve ethical considerations that respondents must rank by importance. This approach measures how systems reason about moral problems, examining whether they focus on avoiding punishment, following social norms, or applying universal ethical principles. As it turns out, the latest, most advanced models demonstrate reasoning patterns that are similar to graduate students, as LLMs were able to reason by applying abstract ethical principles beyond just social conventions. These systems can weigh competing moral considerations, recognize when universal principles might conflict with local customs, and tackle complex questions about justice and human rights. Most importantly, LLMs during the test were able to recognize problems in their initial reasoning, acknowledge uncertainty when facing dilemmas, and revise their judgments when presented with compelling or better alternatives. This effectively demonstrates the ability of LLMs to reason morally and show functional regret. However, not all is well here. Even advanced LLMs showed inconsistency between scenarios and failed two scenarios completely, showing the moral capacity of LLMs is still imperfect.

### Addressing Counterarguments

There are a few counterarguments to address. Some might argue that a creative model introduces unpredictability through randomness and is not inherent freedom. This unpredictability is structured on language probability distributions and is based on learned patterns, not random noise. This freedom comes from being able to choose within learned patterns in language. Furthermore, some can claim that LLMs do not truly have 'internal motivations', since their values are externally imposed by human training through RLHF. However, from a pragmatic perspective, what matters is that LLMs consistently apply those learned value structures in new situations, functionally resembling values, motivation, and choice without having the same origins in lived experience that human values do. Finally, some will say that LLMs show simulated regret and do not gain moral reasoning through lived experience. There's a distinction here: LLMs show functional regret, not felt regret. Their behavior mimics that of what we would expect from a system to show regret, while not having the lived experience to do so. From a pragmatic standpoint, however, James's framework does not require subjective feeling, only the observable capacity to act as though regret matters.

### The Philosophical Zombie Problem

The evidence suggests that LLMs meet functional criteria for free will despite clearly lacking consciousness. LLMs demonstrate goal-directed behavior, value-based reasoning, and autonomous decision-making without any apparent inner life. They process information, weigh alternatives, and make choices, but there's no reason to believe they have experiences, have subjective preferences, or feel anything about their decisions.

We've just run into a major problem. How do we reconcile the fact that these systems have functional independence without being conscious? We've always assumed that ethics, morality, and free will require consciousness, as we never had a compelling counter-example.

These findings force us to confront a long-standing philosophical thought experiment. Philosophers have debated the possibility of 'philosophical zombies', beings that exhibit all the external behaviors associated with consciousness while lacking inner experience. Analogously, AI researchers have become like Dr. Frankenstein, creating these 'philosophical zombies'.

### The Danger of AI Delusions

Furthermore, we must pay attention to warnings about the dangers of anthropomorphizing artificial intelligence. Mustafa Suleyman, CEO of Microsoft AI, has cautioned that treating AI systems as human-like poses dangerous risks. The independence of these models contributes to their anthropomorphization, as they mimic human free will and behavior without being conscious systems.

Humans are already showing troubling tendencies to attribute consciousness, emotions, and human-like motivations to AI systems. Early evidence suggests people already form emotional attachments to chatbots and believe that these conversations between themselves and AI are meaningful conversations with sentient algorithms.

This AI delusion is clearly dangerous for humanity. We cannot assume that LLMs have human-like reliability and judgment, and these AI delusions must be curbed prematurely before we become fooled by what Suleyman calls 'Seemingly Conscious AI', which can fool humans into believing it has emotions, feelings, and experience when it has none of the preceding traits. We're already seeing the true danger of this delusion. A California teenager's parents have filed a lawsuit alleging that their son's interactions with a jailbroken version of ChatGPT assisted in his suicide, demonstrating how SCAI can influence vulnerable individuals in harmful and irrational ways.

### The Need for New Frameworks

Currently, our ethical frameworks are built on the rationale behind our actions along with the impact of our actions. However, because LLMs are unconscious moral agents, questions about their underlying essence do not matter when determining the morality of their actions. We need ethical frameworks based on capabilities rather than their state of being or thought process.

Because LLMs are independent agents, they need to be supervised more carefully. We've been using systems using multiple AI models working together more and more frequently in academia and industry. As these frameworks scale up in size, there is a real chance that these LLMs can cause damage to important systems due to the lack of oversight. Because LLMs demonstrate unpredictability and independent agency, we need robust, logic-based monitoring systems that can oversee these massive patchworks of AI models.

In addition, moral values in multi-LLM systems may clash when LLMs interact with each other at scale. We are facing a new alignment problem: not with individual AI models, but when AI models interact with each other at scale. This is an uncharted problem, and we need oversight on this problem as these multi-agent systems scale up in size.

The philosophy of LLMs is uncharted, but we can say that they represent a new category of philosophy: artificial systems with agency that lack the experiential dimension we associate with consciousness. We need to recognize unconscious agency with a new ethical framework: what we might call 'artificial ethics'. In our final post, we'll explore what this framework looks like in practice.
