---
layout: post
title: A model of traffic congestion
use_math : true
published: true
date:  July 3, 2021
author: Kaining Zhang
tags: [random, Math, traffic]
---

This post is for an old thought of mine. The idea came to my mind when I was blocked in traffic congestion on the highway. I saw the cars around me stopped and moved, which motivated me to do some modeling of the traffic congestion. Later I found that a more general model has already been found, and it is called the "Lighthill-Whitham-Richards traffic flow model"<sup>1</sup>.

When there is local congestion, the cars in the back drive into the congestion area, and the cars in the front drive out of the congestion area. In the meantime, the congestion area gradually moves toward upstream of the traffic. This phenomena is called traffic wave<sup>2</sup>.

To model the traffic wave, I need to first make some simplifications.
Here I only consider a road with one line. The average car length is $b$.
And all drivers follow the 3-second rule: when someone is driving, the distance between his/her vehicle and the vehicle in front of him/her should be at least 3 seconds times his/her speed. This rule determines the relation between a vehicle's speed and the distance between the vehicle and its previous vehicle.

$$ a* v \leq L \text{, where } a = 3s \qquad \text{(1)}$$

When the traffic is heavy, the inequality becomes equality. 

$$ a* v = L \text{, where } a = 3s \qquad \text{(2)}$$


By (2), we can derive a relationship between the speed of cars at a spot and the density of the cars around that spot.

$$ d_{car} = \frac{1}{L+b} =\frac{1}{av+b} \qquad \text{(3)}$$

I.e.

$$ v = \frac{1}{a* d_{car}} - \frac{b}{a} \qquad \text{(4)}$$

Now we can use (4) and the principle of conservation of mass in fluid mechanics to write down the equation.

the principle of conservation of mass gives the equation: 

$$ \frac{\partial d_{car}}{\partial t} =  -\frac{\partial (v * d_{car})}{\partial x} $$

Substitute $v$ with (4).


$$ \frac{\partial d_{car}}{\partial t} = -\frac{\partial ((\frac{1}{a* d_{car}} - \frac{b}{a})* d_{car})}{\partial x} $$

And simplify it:

$$ \frac{\partial d_{car}}{\partial t} = \frac{b}{a} \frac{\partial d_{car}}{\partial x} \qquad \text{(5)}$$

Equation 5 has the general solution:

$$ d_{car} = f(x + \frac{b}{a} * t) $$, where $$ f(\cdot) $$ can be arbitrary $$ C^1 $$ function.


This solution shows that the density of the cars moves with speed $ \frac{b}{a} $ in the opposite direction of the cars. (Traffic wave)


Lastly, we can substitute $a$ and $b$ with actual numbers, the average length of a car is about $4.5m$, and we should also include the distance between the cars when they stop, and roughly on average it is about $2m$. So $b = 4.5m+2m = 6.5m$.


And $a = 3s$, by the 3 second rule.


So, in theory, the speed of the traffic wave is about $ 6.5m/3s \approx 2.2m/s \approx 5 mph $. 

Here is a visualization of the solution:
<p align=center>
<img src="\assets\image_for_notes\traffic_congestion\figure-2.jpg" alt="Figure 1" width = "900" align="center">
<p/>


In reality, the actual speed of traffic wave is higher than this<sup>3</sup>, and one of the reasons could be that my estimation a = 3s is higher than the rule that people actually use in traffic congestion. <br/><br/>


In Lighthill-Whitham-Richards traffic flow model, it didn't use the 3 second rule. Instead, it directly gives a nonlinear relation between the traffic flow ($ v * d_{car} $) and the density ($ d_{car} $).<sup>1</sup> 
And if the relationship between the traffic flow and the density is linear, then the Lighthill-Whitham-Richards traffic flow model converges with the model in this post.






<h3>Reference:</h3>

[1]. https://sboyles.github.io/teaching/ce392d/5-lwrmodel.pdf<br />

[2]. https://wikiwaves.org/Traffic_Waves<br />

[3]. https://www.youtube.com/watch?v=Suugn-p5C1M<br />

[4]. https://www.springer.com/gp/book/9783540207160<br />

[5]. https://www.fhwa.dot.gov/publications/research/operations/tft/chap5.pdf<br />



