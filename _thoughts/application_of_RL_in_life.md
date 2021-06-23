---
layout: post
title: Modelling life as an optimization problem
use_math : true
published: true
date:  June 20, 2021
author: Kaining Zhang
tags: [random, optimization]
---

"Life is an optimal control problem."

The professor said the line in an optimal control class.

If life is an the optimal control problem, first of all, we need to define an objective function for it.
At first glance it may look hard to find an universal objective function for every one, different people have different goals in their life. 

Some people want to travel around the world, some people want to be famous, some people want to help the poor people, some people want to get out of the miserable environment they have been lived in.
The goals of life varies from person to person, but biologically it is usually the happiness and satisfaction during or after pursuing the goals that motivates people's behavior. Most of the people want to be happy and fulfilled in most days of their life and avoid unhappiness.


By this observation, I try to generalize most people's goal of the life using an universal objective function:

$$ \int_{birth}^{death} happiness\ dt \quad \text{(1)}$$

This is the integration of a person's happiness throughout his/her life span, the value of happiness can be negative, which represents unhappiness.

The hypothesis is that throughout the life, human try to maximize this objective function, and the constraints of the maximization includes physical laws, biological constraints, social norms, etc. etc. 

Happiness is very subjective feeling and has no accurate behavior measurement. In the next few paragraphs I try to quantified happiness using reward prediction error (RPE), and further more, quantify it in money-form.

Biologically happiness is close related to reward, or more precisely, reward prediction error(RPE), aka, actual reward minus expected reward(cite). This concept is first introduced in reinforcement learning and later people found RPE are explicitly signaled in the brain by midbrain dopamine neuron.<sup>1-3</sup>

When a person gain something, (s)he gets happy, but after a while the happiness faded away. Happiness is usually a transient signal, just like reward prediction error signal of the midbrain dopamine neurons. 
We may also experience this phenomenon. The happiest moment is when we heard the good news of an event, rather than the experience of the event itself. RPE behaves exactly the same. When a person heard the good news. the future outcome becomes better than (s)he expected, RPE signal suddenly deviates from 0 and become positive transiently. However, when (s)he actually experience the event. If it is the same as (s)he expected, then the RPE signal remains almost 0.

If we assume happiness is proportional to reward prediction error, then the objective function becomes

$$ \int_{birth}^{death} happiness\ dt  \propto \int_{birth}^{death} RPE\ dt \quad \text{(2)}$$

**Noted, The integral of RPE is simply the total amount of reward gains minus the total amount of reward losses in ones life span** .

Albeit, RPE is still hard to measure. Although it is explicitly signaled by some midbrain dopamine neurons in each individuals, we can't just open a random person's brain and record the neurons. So the next step is to find another measurement which is easy to access, and reflects RPE or reward gains/losses. And a good candidate is money, which explicitly measures the value of goods. A rational person will buy something only if he thinks the price is lower than or equal to his/her subjective value of that thing. So a person's reward gain strongly correlates with this person's money consumption. Reward loss is a little bit more complex, the premise that someone can loss some reward or have reward lower than (s)he has expected is that at some previous point, (s)he gain the reward or reward expectation. Thus, the reward loss should cancel out some of the previous reward gain.

The formula of the objective function I proposed is:

$$ \sum_{life\ span} money\ earned\ - \sum_{life\ span} money\ lost \quad \text{(3)}$$

The money earned term should include, for example, salary, interests, gifts, heritages, etc. etc.
The money lost term should include, for example, the value of the goods (s)he accidentally breaks, the money being robbed, etc. etc., and importantly, the money left unspent when (s)he die.
The difference between the two terms is all the money that the person consume to gain happiness in his/her life span.

**Note 1**. I can also add some terms in the objective function (1) to simulate a person's altruism.

$$ \int_{birth}^{death} my\ happiness\ dt + \sigma_1 \int_{birth}^{death} person\ 1's\ happiness\ dt + \sigma_2 \int_{birth}^{death} person\ 2's\ happiness\ dt\ +\ ... \quad \text{(4)}$$

$\sigma_i$ determines how much "I" care about the other people, and $\sigma_i$ can be generally positive(altrustic) or negative(anti-social).

**Note 2**. To get the objective function (3) from (1), many assumptions have been made and all the equations above are only roughly equal. For example, when I use a lower price and buy something I like a lot, in this situation the money can't accurately measures my happiness. Another counterexample, the reward gains also includes other none money-form, for example, knowledge, fames, compliment from others, etc. Another counterexample, People's mood can go up and down chronically and is not encoded in the midbrain dopamine neuron's RPE signal, but it is correlated with people's happiness.

**Note 3**. Ultimately, I proposed that the objective function of life is (1) rather than (3). If someone only sees and optimizes (3), (s)he can easily fall in the trap of consumerism<sup>4</sup>. 




After we set up the objective function, the next thing is how should we optimize it? For simple optimal control problem, researchers have developed many methods to solve it, including Monte Carlo, reinforcement learning, Pontryagin's maximum principle (analytical solutions), etc ... For the optimization problem of life, normal humans actually intrinsically use a mixture of algorithms that researchers have defined. And the algorithms varies from people to people, and from scenario to scenario. Sometimes people adjust their behavior by observing and mimicking previous people's success. (kind of similar to Monte Carlo alg.) Sometimes people learn through trying by themselves and learn from errors and hits. (kind of similar to reinforcement learning alg.) Sometimes people analysis the situation and make plans before behaving. (kind of similar to solving the problem analytically).

The optimization problem of life is an normative theory in the sense that it only says that people try to pursue the optimal behavior, but not necessarily restrict people's behavior to be optimal, aka, it allows suboptimal behavior. For example, a drug addict may choose to have instinct pleasure when using drugs which will result in much more unhappiness during the rest of his/her life. Suboptimal behavior is very common in most of the people as well and people usually call it irrational behavior. For example, someone may be attracted to a fancy advertisement and buys some useless products. After all, what a difficult problem it is to optimize a function throughout ones life span in a very high dimensional space with a lot of uncertainty. None of current algorithms can find the exact result.


Seeing life as an optimization problem with objective function as (1) or (3) can explain some behavior of many people.

<h3>1. Why should we work? </h3>

It is true that some people can gain happiness in their work. But for most of the people, it is the salary rather than the happiness during work that sustains their working behavior. People earn money, so that after work they can consume it on things they like, and enjoy happiness.

Here I solve an very simplified case of the work-life balance problem in the framework of the optimization problem of life.

Work-life balance problem: Ideally, how many hours should a person spend in working, and how many hours should s(he) spend in enjoying life?


Assuming there is a person Alice, he has no other income source besides his salary which is proportional to his working time, and he feels neither happy or sad during work. He wants to know the proposition of time his should distributes between working and enjoying life. Here I denote the set of time for work by $\tau_{work}$, the total length of time for work by $T_{work}$, the set of time for enjoying life by $\tau_{nowork}$, and the total length of time for enjoying life by $T_{nowork}$, $T_{work} + T_{nowork} = T_{life}$, $T_{life}$ is the total length of time he can distribute, which is a constant. 


we assume Alice's job can earn $r_{earn}$ dollar per hour, and during nonworking time, Alice's happiness is porportional to the rate of money his spent per hour, $happiness \propto r_{spend} $. Also to prevent the money spending rate goes to infinite (in life, this constraint means that he need time to enjoy the food/travel/games that he have bought), we add the constraint that $ r_{spend}(t)< r_{max}, t\in \tau_{nowork}$. Another constraint is that Alice can't spend more money that what he earns.

With these conditions, the optimization problem can be summarized as: Find $T_{nowork}(\tau_{nowork})$ and $r_{spend}(t)$ defined on $\tau_{nowork}$ such that the following function reaches maximum.

$$\int_{\tau_{nowork}} r_{spend}(t)\ dt$$ 

With the constraints: 

$$
\begin{aligned}
& \int_{\tau_{nowork}} r_{spend}(t)\ dt  \leq \int_{\tau_{work}} r_{earn}(t)\ dt \\
& T_{work} + T_{nowork} = T_{life} \\
& r_{spend}(t)< r_{max}, t \in \tau_{nowork}\\
\end{aligned}
$$


For this very simplified case, the solution can be easily found: 

$$
\begin{aligned}
& r_{spend(t) = r_{max}, t \in \tau_{nowork}\\
& T_{nowork} = T_{life}* r_{earn}/(r_{max}+r_{earn}) \text{, aka, } T_{work}: T_{nowork} = r_{max}: r_{earn}\\
\end{aligned}
$$

Interpretation: 

(1) From the solution we have $$ \int_{\tau_{nowork}} r_{spend}(t)\ dt  = \int_{\tau_{work}} r_{earn}(t)\ dt$$, aka, Alice should spend all the money he earns before death.

(2) $$r_{spend}(t) = r_{max}$$. Alice should spend his money as fast as possible in the non working time.

(3) A consequence of (1) and (2) is that Alice should work as long as possible to earn the money he can spend.
Summarizing (2) and (3), I call it "work long, play hard" strategy.

(4) The more Alice earned per hour (higher $r_{earn}$), the less time his should spend on working.

**Note 4**. This model is overly simplified, and many factors in real life are overlooked. For example, there are certain time period that people can't work (when they are young or old); People may want to leave some money to their offspring instead of consuming them all; The precise number of $r_{max}$ is hard to find, etc. etc.

Although quantitative the model is not accurate, but qualitative I do find some people in certain career automatically appreciate and practice some part of the solution. For example the "work long(hard), play hard" strategy, and the principle of "spending all the money before you die".



<h3>2. Why do parents always supervise their children's behavior?</h3>

There are two things that may make the optimization problem fail to model children's behavior. 

(1) The meaning of happiness for children may change relatively quickly and can't be measured in money-form. A newborn baby only knows eat, drink, seeking parents hug, etc., but as his/her knowledge grow, (s)he starts to find other things that can make him/herself happy. 

(2) (This  is related to the question of the section.) The ability of children to solve the optimization problem is usually weaker than adults. For example, they may more relay on the pre-wired biological algorithm to pursue instant satisfactory and have little sightseeing of the future. 
In order to help a child to 1) improve the child's objective function itself, 2) improve the child's optimization algorithm, interference is needed in the early stage of life from a person who has better optimization algorithms. 

Parents behavior can be described using the objective function: 

$$ \int_{birth}^{death} my\ happiness\ dt + \sigma_1 \int_{birth}^{death} child\ 1's\ happiness\ dt + \sigma_2 \int_{birth}^{death} child\ 2's\ happiness\ dt\ + ... \quad \text{(5)}$$

Inside the parent's objective function, children's integrals of happiness are also included. In order to optimizing their own objective function of life, parents will exert control to help the children to find a better solution of their lives.

For example, I observe that parents like to force their children to study even if the children don't want to. The behavior of studying may not create big instant happiness (sometimes even very negative feelings). However it creates much more happiness in their adulthood by providing more choices in career and on average higher salaries. However, not all people in their childhood can realize the benefits and implement this better optimized behavior. So the job for the parents is to overwrite the children's algorithm, aka be against the children's will and push them to study. 

By Kaining


<h3>Reference:</h3>
[1]. Sutton, R.S. and Barto, A.G., 2018. Reinforcement learning: An introduction. MIT press.<br />
[2]. Schultz, W., Dayan, P. and Montague, P.R., 1997. A neural substrate of prediction and reward. Science, 275(5306), pp.1593-1599.<br />
[3]. Bromberg-Martin, E.S., Matsumoto, M. and Hikosaka, O., 2010. Dopamine in motivational control: rewarding, aversive, and alerting. Neuron, 68(5), pp.815-834.<br />
[4]. https://en.wikipedia.org/wiki/Consumerism<br />
[5]. An interesting discussion Binxu and I have had about persistency: [link](https://animadversio.github.io/personal%20writing/2021/01/15/A-model-of-Persisitency.html)<br />
