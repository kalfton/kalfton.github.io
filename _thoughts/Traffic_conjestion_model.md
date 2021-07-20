---
layout: post
title: A model of traffic conjestion
use_math : true
published: true
date:  July 3, 2021
author: Kaining Zhang
tags: [random, Math, traffic]
---

This post is for an old thought I had about 2 years ago. The idea started when I was blocked in a traffic conjestion on the high way. I saw the cars around me stopped and moved, which motivates me to do some modelling of the traffic conjestion. Later I found that a more general model has been studied before and has a name called "Lighthill-Whitham-Richards traffic flow model"<sup>1</sup>.

When there is a local conjestion, the cars in the back drive into the conjestion area, and the cars at the front drive out of the conjestion area. In the meantime, the conjestion area gradually moves toward the upstream of the traffic. This phenomena is called traffic wave<sup>2</sup>


To model the traffic wave, firstly I need to make some simplification of the reality.
(Assumptions) Here we consider a road with one line. The average car length is $b$.
We have the three-second rule: when someone is driving, the distance between his/her vehicle and the vehicle in front of him/her shound be at least 3 seconds times his/her speed. This rule determines the relation between a vehicle's speed and the distance between the vehicle and its previous vehicle.

$$ a* v \leq L \text{, where } a = 3s \qquad \text{(1)}$$

When the traffic is heavy, the inequality becomes equality. 

$$ a* v = L \text{, where } a = 3s \qquad \text{(2)}$$


By (2) we can derive an relationship between the speed of a car and the density of the the cars around the place of the car.

$$ d_{car} = \frac{1}{L+b} =\frac{1}{av+b} \qquad \text{(3)}$$

or we can write the speed of car $v$ at a specific place as a function of car density($d_{car}$) 

$$ v = \frac{1}{a* d_{car}} - \frac{b}{a} \qquad \text{(4)}$$

Now we can use the conditions given above and the principle of conservation of mass in fluid mechanics to write down the equations.

the principle of conservation of mass gives the equation: 

$$ \frac{\partial d_{car}}{\partial t} =  -\frac{\partial (v * d_{car})}{\partial x} $$

substitute $v$ with equation 4.


$$ \frac{\partial d_{car}}{\partial t} = -\frac{\partial ((\frac{1}{a* d_{car}} - \frac{b}{a})* d_{car})}{\partial x} $$

And simplify it:

$$ \frac{\partial d_{car}}{\partial t} = \frac{b}{a} \frac{\partial d_{car}}{\partial x} \qquad \text{(5)}$$

Equation 5 has an general soluton:

$$ d_{car} = f(x + \frac{b}{a} * t) $$, where $$ f(\cdot) $$ can be arbitary $$ C^1 $$ function.


The density of the car moves in the opposite direction of the cars with the speed $ \frac{b}{a} $.(Traffic wave)


Lastly, we can substitute $a$ and $b$ with numbers, the average length of a car is about 4.5m, and here we should include the distance between the car when they stopped. Let's say it is 2m. So b = 4.5m+2m = 6.5m.


And a = 3, by the 3 second rule.


So we got that the speed of traffic wave is about $ 6.5m/3s \approx 2.2m/s \approx 5 mph $. 

The visualization of the solution is here:
<p align=center>
<img src="D:\Users\Kaining\Documents\GitHub\kalfton.github.io\assets\image_for_notes\traffic conjestion\figure-2.jpg" alt="Figure 1" width = "600" align="center">
 <p/>


In reality, the actual speed of traffic wave is higher than 5mph<sup>3</sup>, and one of the reason could be that the estimation a = 3s is higher than the rule that people actually use.
 



<h3>Reference:</h3>

[1]. https://sboyles.github.io/teaching/ce392d/5-lwrmodel.pdf<br />

[2]. https://wikiwaves.org/Traffic_Waves<br />

[3]. https://www.youtube.com/watch?v=Suugn-p5C1M<br />

https://www.springer.com/gp/book/9783540207160<br />

https://en.wikipedia.org/wiki/Traffic_wave<br />

https://www.fhwa.dot.gov/publications/research/operations/tft/chap5.pdf<br />




