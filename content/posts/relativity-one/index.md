---
title: "Relativity 1: Pre-Einstein"
author: "Rohan Arni"
date: 2024-07-15T09:10:42-05:00
draft: false

subtitle: ""
math: true

categories: ["Science", "Physics"] 

---

*Note to reader: This is the first in a series.*

Relativity, we've heard so much about it. Created by Einstein, it's lived in the minds of both physicists and the cultural zeitgeist. It's the idea behind black holes, time travel, and has single-handedly spawned off so many Hollywood movies.

To truly understand the beauty of special relativity, we must go back in time. Relativity is not a new concept that Einstein created; it's been around since the time of Galileo and Newton. So what was this "original" relativity? Well, let's understand what relativity even means. 

Suppose I am standing still, and you are walking at a constant speed ($u$) to the right. This places us in two separate "reference frames" (ways of looking at the universe). We can call both reference frames "inertial", because in both cases, there is no net force/acceleration acting upon either of us ($\Sigma F = 0$). Relativity states that the same laws of mechanics work in all inertial reference frames, independent of frame velocity. But how can we come to this conclusion? Well, let's go back to our original scenario. 

Say we set our "zero" point when you and I cross the same position. Some time ($t$) away, a firecracker goes off. We both see the firecracker, but we see it from different reference frames. You have traveled some distance $d=ut$ (where $d$ is the distance you traveled, $u$ is your velocity, and $t$ is the time of the event), but I am still at the inital point. I can give it some description for position and time $(x, t)$, and you can give it a description $(x', t')$. We can draw it out:

![image](images/graph1.excalidraw.png#layoutTextWidth)

Now, we have our scenario fully established. In our world, our times are the same ($t' = t$). We can also see the relationship between $x'$ and $x$ from the drawing:

$$
x = x' + ut $$

We can rearrange the first statement and write the two equations:

$$ x' = x - ut \\ t' = t $$

We call this the Galilean Transformation. Really take the time to understand this scenario, as it is the basis for everything to come after. 

But if we're seeing with two different coordinates, how can we have the same laws of mechanics for both situations? Let's take a look at the most important one: $F=ma$. We have a function for position, we just need to find one for velocity and acceleration. For the velocities, we take the derivative of both sides (the rate of change):

$$
v'=\frac{dx'}{dt}=\frac{dx}{dt}-\frac{d}{dt}(ut) 
$$

Since the derivative of position is velocity and the derivative of $ut$ with respect to $t$ is $u$, we get:

$$
v' = v - u
$$

Now, for acceleration, we do the same thing again:

$$
a' = \frac{dv'}{dt}=\frac{dv}{dt}-\frac{d}{dt}(u)
$$

Since the derivative of velocity is acceleration and the derivative of $u$ with respect to $t$ is 0 (derivative of a constant is 0), we get:

$$
a' = a - 0 \\
a' = a
$$

So, our accelerations are the same! Therefore, 
$$
F' = ma' \\
F = ma \\
F' = F \\
$$
We have proven that our forces are the same regardless of the reference frame (as long as it is inertial).

This was the understanding of relativity in the old days. The world was happy, and it made sense. This was about to change very quickly, as in 1905, a patent clerk would publish a paper that would change the world.