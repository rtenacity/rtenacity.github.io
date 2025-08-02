---
title: "Rockets and Momentum"
author: "Rohan Arni"
date: 2025-08-01T00:00:00-05:00
math: true

categories: ["Science", "Physics", "Math"]
---

Let's take a look at how a rocket works, based on only concepts from momentum. The basic idea is that we have a system of rocket and fuel with mass $m$ and velocity $v$. If we burn fuel and eject mass, we will gain velocity. But how can we quantify this relationship? Let's begin with the derivation of the famous Tsiolkovsky rocket equation. 

To begin, let's identify the initial state of our system. At some time $t_i$, we have the momentum of our system as

$$p_i = mv$$

This is the standard formula for momentum. Now, let's imagine at some time $t_i + dt$ later, we lose some small mass of fuel $dm$ and gain some velocity $dv$. We eject the fuel at some exhaust speed $v_e$ relative to our rocket ship. The momentum of our system is now:

$$p_f = (m-dm)(v+dv) + (dm) (v-v_e)$$

By expanding, we get

$$p_f = mv - vdm + m dv -dm dv + vdm - v_e dm$$

By assuming the rule that the product of two infinitesimally small quantities $\approx 0$ and simplifying, we get

$$p_f = mv  + m dv - v_e dm$$

Now, by conservation of momentum, $p_i = p_f$. From this, we get the cancellation of the $mv$ term and get

$$v_e dm = m dv$$

Now, we want to solve for the velocity evolution over time. We also know that $dm$ is a negative quantity, so we can rearrange and write explicitly

$$ dv = - v_e \frac{dm}{m}$$

Now we just solve by integrating the left hand side by velocity and the right hand side by mass. Basically, we're summing up the tiny quantities in the equation. 

$$\int_{v_0}^{v_f} dv = - v_e \int_{m_0}^{m_f} \frac{1}{m} dm $$

$$ v_f - v_0 = v_e \ln \left(\frac{m_0}{m_f}\right)$$

$$ \Delta v = v_e \ln \left(\frac{m_0}{m_f}\right)$$

Congratulations, we've proved that the velocity will change at a logarithmic scale! Thanks for reading this ramble, I wanted to write about something but it's 12AM and I'm barely alive :)


---