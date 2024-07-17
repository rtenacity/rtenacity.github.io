---
title: "Relativity 2: Enter Einstein"
author: "Rohan Arni"
date: 2024-07-16T09:10:42-05:00
draft: false

subtitle: ""
math: true

categories: ["Science", "Physics"] 

---
*Note to reader: if you have not read part one, do so [here](https://rohanarni.com/posts/relativity-one).*

So, what was wrong with Galilean relativity? It help up perfectly well, until a Scottish mathematician by the names of James Clerk Maxwell created his four namesake laws of electricity and magnetism. As a consequence of his laws, he was able to derive the speed of light in a vacuum, which was given the variable $c$. 

Now, according to Galilean relativity, the speed of light seen by a moving observer should be the speed of light minus the moving observer:

$$ v = c - u $$

We can rewrite that principle and say that if light is emitted from a moving source, its speed should be $c$ plus the speed of the source relative to the observer:

$$ v = c + w$$

Where $v$ is the velocity of light seen by the observer and $w$ is the velocity of the moving source. Unfortunately, this is not what happens. In 1887, Michelson and Morley ran their famous experiment searching for the "ether", the mysterious medium that light was supposed to propagate through. They found, however, that there was no variation in the speed of light, which goes against Galilean relativity. 

This was a disaster! Scientific theories that had been held for hundreds of years were just disproven in an instant. Clearly, something needed to be done. 

This is what Einstein set out to do. In his 1905 paper "On The Electrodynamics of Moving Bodies", he wrote down the two postulates of special relativity. 

1. All inertial observers are equivalent. All inertial observers are equally privileged to discover and observe natural phenomenon.
2. The velocity of light is independent of the state of motion of the source or the observer.

(A warning: the next section is a bit math heavy, but don't get scared! It's not terribly hard to follow along. If it doesn't make sense, skip it, as the big conclusions are at the end.)

From these two postulates, we can begin to formulate special relativity.  We now know that times are no longer constant, so we get:

$$ x'=x-ut \\ 
x=x'+ut'$$

Since the only constant between two observers is the speed of light, even lengths do not remain the same between observers. Therefore, we need to introduce some factor $\gamma$:

$$x'=\gamma \left(x-ut\right) \\
x=\gamma (x'+ut')$$

But what is this factor? Well, we must come up with a scenario first. Imagine, instead of a firecracker, a light-pulse traveling at a velocity $c$. I observe it at $(x, t)$, and you observe it at $(x', t')$. Therefore:
$$ x = ct \\ x' = ct'$$

This is because we only agree on the speed of light. Now, armed with all 4 equations, we can derive our factor $\gamma$.

1. Start with our initial equations:
$$ 
x' = \gamma(x-ut) \\\ \\\
x= \gamma(x'+ut')
$$

2. Multiply both equations together:
$$ xx'=\gamma ^2\left(xx'+xut'-x'ut-u^2tt'\right) $$

3. Substitute for x and x':

$$ c^2tt'=\gamma ^2\left(c^2tt'\ +uctt'-uctt'-u^2tt'\right)$$

4. Simplify:

$$ c^2tt'=\gamma ^2tt'\left(c^2-u^2\right) \\\ \\\ c^2=\gamma ^2\left(c^2-u^2\right) $$

5. Solve in terms of $\gamma$:

$$
\gamma ^2=\frac{c^2}{c^2-u^2} \\\ \\\ 
\gamma ^2=\frac{1}{1-\frac{u^2}{c^2}} \\\ \\\ 
\gamma =\frac{1}{\sqrt{1-\frac{u^2}{c^2}}} $$

Bingo! That's our factor, which we call the Lorentz factor. Now, we can plug this in to our equations and get the Lorentz transformations:

$$ x'=\frac{x-ut}{\sqrt{1-\frac{u^2}{c^2}}} \\\ \\\
t'=\frac{t-\frac{ux}{c^2}}{\sqrt{1-\frac{u^2}{c^2}}} $$

So this is great, but what does all of this stuff even mean? Well, first of all, we can't take distance or time for granted anymore, as they can be different for different observers. Thankfully, we also find that if $u$ is not close to the speed of light, these equations just break down back into good old Galilean transformations. See below:

$$ x' = \frac{x-ut}{\sqrt{1-0}} \approx x-ut$$

$$ t' = \frac{t-\frac{0x}{c^2}}{\sqrt{1-0}} \approx t$$

So this is good news! Our old ways of thinking hold up at small velocities.

Regardless, $(x, t)$ and $(x', t')$ all cover the same space-time interval, a combination of distance and time. The space-time interval is invariant, meaning it does not change for all observers. As a result, the Lorentz transformations are invariant transformations, as they do not deform space-time.

Does your head hurt yet? Mine sure did when I first read about all of this. Don't worry, it just gets weirder from here...