---
layout: post
title: A force analysis of Skiing (or Snowboarding)
use_math : true
published: true
author: Kaining Zhang
date:  Dec. 4th, 2022
tags: [random]
---

When skiing downhill, skiers use turns to control their speed. During each turn, they must **switch edges** and **move their body up and down** to apply periodic force to the skis, thereby modulating their speed.

There are two primary techniques to control this periodic force: **upweighting** and **downweighting**, which seems to give opposite instructions. Here I want to unify this two techiques, and explain why they seems to be different.

To understand this process, I model the force applied to the skis as a periodic function (considering only the vertical direction). For simplicity, I use a cosine wave to represent the force the skier applies to the board:

$$
f(t) = \cos(\omega t) + C_0 \tag{1}
$$

To keep the speed roughly constant, the skier must make turns. During this process, the vertical force should **maximized during the turn** and **minimized during the edge switch**. This is a universal law in skiing.

Let $mg$ denote the gravitational force. The skier’s vertical speed $v(t)$ can be approximated by integrating the net vertical force:

$$
v(t) = \int (f - mg) \, dt = \frac{1}{\omega} \sin(\omega t) + (C_0 - mg)t + C_1 \tag{2}
$$

For the skier’s speed to remain stable and periodic, we require:

$$
v(t) = v(t + T), \quad \text{where } T = \frac{2\pi}{\omega}
$$

This periodicity condition implies $C_0 = mg$, simplifying equation (2) to:

$$
v(t) = \frac{1}{\omega} \sin(\omega t) + C_1 \tag{3}
$$

Integrating once more, we obtain the vertical position of the skier's center of gravity, $x(t)$:

$$
x(t) = \int v(t) \, dt = -\frac{1}{\omega^2} \cos(\omega t) + C_1 t + C_2 \tag{4}
$$

Comparing equations (1) and (4), we see that the periodic components are **out of phase**: when the applied force is maximized (i.e., during a turn), the center of gravity is at its lowest. Conversely, during edge switching (when force is minimized), the center of gravity is highest.

---

In practice, the skier **move their center of gravity up and down** to generate the desired pressure on the skis. This leads to two contrasting techniques:

* **Upweighting**: The skier raises and lowers their **upper body** to control the center of gravity. During the transition between turns, the skier’s body is extended, as they lift their upper body to raise their center of gravity.

* **Downweighting**: The skier bends and extends their **lower body** (i.e., legs) to modulate the center of gravity. In this technique, the skier is bent during transitions, as they raise their legs up to raise their center of gravity.

Both methods aim to manipulate the skier’s weight distribution to control the pressure on the skis—but they involve **opposite body movements**.

---

