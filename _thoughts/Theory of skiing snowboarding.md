---
layout: post
title: Theory of Skiing (Snowboarding also apply)
use_math : true
published: false
author: Kaining Zhang
date:  Dec. 4th, 2022
tags: [random]
---

Two skiing techniques: Upweighting and downweighting

(Intro:)

When people do downhill skiing, they use turns to control the speed.
When turning, they need to swith edges and the move their body up and down, in order to apply periodic forces to the board to control the speed.


(A picture of S-shape skiinng trail)


This can be simplied and explaned by the following model:

The periodic force applied to the ski board can be simplified as a cosine function:
$$ f = cos(\omega t) + C_0    (1) $$

In order to control (decrease) the speed, the force should be maximized in the turning and thus minized when swithing edges.


Then we have $$ v(t) = \int f - mg  = 1/\omega* sin(\omega t) + (C_0-mg)t + C_1   (2)$$ where mg is the gravity force.
If the speed control is good, the human should has periodic speed, which add the condition that $$ v(t) = v(t+T) $$, $$ T = 2 \pi/omega $$
This requires $$ C_0=mg $$, so v(t) is simplified as:
$$ v(t) = \int f - mg  = 1/\omega* sin(\omega t) + C_1   (3) $$

Then the position of the weight centric x(t) =  \int v = -1/\omega^2 cos(\omega t) + C_1 t + C_2      (4) $$

By comparing (1) and (4), we can see that the periodic term are inverse of each other, which means that when turning, the weight centric should be low, and in contrast, the weight centric should be high during switching.

(figure)

In skiing, the controlling is this other direction: People actually moves the weight centric position to apply various forces to the board.
There are two ways to control the weight centric, one is called upweighting, the other is called downweighting.

(Introduce what are upweighting and downweighting, put a video link with them.) 

If we separate human by upper body and lower body, the upweighting way is to move the upper body up and down to make the weight centric up and down, where the downweighting way is to move the lower body up and down to make the weight centric up and down.(figure.)













To dos:
What is the relationship of friction and energy consuming with the angle of the board?

