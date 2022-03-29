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

Professor Schaettler said the line in the class when he talked about optimal control in economics.

If life is an optimal control problem, first of all, we need to define an objective function for it.
At first glance, it may look hard to find a universal objective function for everyone; different people have different goals in their life. 

Some people want to travel around the world; some people want to be famous; some people want to help the poor people; some people want to get out of the miserable environment they have been living in.
The goals of life vary from person to person, but biologically it is usually the happiness and satisfaction during or after pursuing the goals that motivate people's behavior. Most people want to be happy and fulfilled on most days of their life and avoid unhappiness.


By this observation, I try to generalize most people's goal of the life using an universal objective function:

$$ \int_{birth}^{death} happiness\ dt \quad \text{(1)}$$

This is the integration of a person's happiness throughout his/her life span; the value of happiness can be negative, which represents unhappiness.

The hypothesis is that throughout life, human try to maximize this objective function, and the constraints of the maximization include physical laws, biological constraints, social norms, etc., etc. 

Happiness is a very subjective feeling and has no accurate behavior measurement. In the next few paragraphs, I try to quantify happiness using reward prediction error (RPE), and furthermore, quantify it in the money form.

Biologically happiness is closely related to reward, or more precisely, reward prediction error(RPE), aka, actual reward minus expected reward. This concept was first introduced in reinforcement learning, and later people found RPE were explicitly signaled by the midbrain dopamine neuron in the brain.<sup>1-3</sup>

When a person gains something, (s)he gets happy, but after a while, the happiness fades away. Happiness is usually a transient signal, just like the reward prediction error signal of the midbrain dopamine neurons. 
We may also experience this phenomenon. The happiest moment is when we hear the good news of an event rather than the experience of the event itself. RPE behaves exactly the same. When a person hears good news, the future outcome becomes better than (s)he expected, RPE signal transiently becomes positive. However, when (s)he actually experience the event. If it is the same as (s)he expected, then the RPE signal remains almost 0.

If we assume happiness is proportional to reward prediction error, then the objective function becomes

$$ \int_{birth}^{death} happiness\ dt  \propto \int_{birth}^{death} RPE\ dt \quad \text{(2)}$$

**Noted, The integral of RPE is simply the total amount of reward gains minus the total amount of reward losses in one's life span** .

Albeit, RPE is still hard to measure. Although it is explicitly signaled by some midbrain dopamine neurons in each individual, we can't just open a random person's brain and record the neurons. So the next step is to find another measurement that is easy to access and reflects RPE or reward gains/losses. And a suitable candidate is money, which explicitly measures the value of goods. A rational person will buy something only if he thinks the price is lower than or equal to his/her subjective value of that thing. So a person's reward gain strongly correlates with this person's money consumption. Reward loss is a little bit more complex. The premise that someone can lose some reward is that (s)he gains the reward or reward expectation at some previous point. Thus, the reward loss should cancel out some of the previous reward gains.

The formula of the objective function I proposed is:

$$ \sum_{life\ span} money\ earned\ - \sum_{life\ span} money\ lost \quad \text{(3)}$$

The money earned term should include, for example, salary, interests, gifts, heritages, etc., etc.
The money lost term should include, for example, the value of the goods (s)he accidentally breaks, the money being robbed, etc., and importantly, the money left unspent when (s)he dies.
The difference between the two terms is all the money that the person consumes to gain happiness in his/her life span.

**Note 1**. I can also add some terms in the objective function (1) to simulate a person's altruism.

$$ \int_{birth}^{death} my\ happiness\ dt + \sigma_1 \int_{birth}^{death} person\ 1's\ happiness\ dt + \sigma_2 \int_{birth}^{death} person\ 2's\ happiness\ dt\ +\ ... \quad \text{(4)}$$

$\sigma_i$ determines how much "I" care about the other people, and $\sigma_i$ can be generally positive (altruistic) or negative (anti-social).

**Note 2**. From (1) to (3), many assumptions have been made, and all the equations above are only roughly equal. For example, when I use a lower price and buy something I like a lot, the money can't accurately measure my happiness. Another counterexample, the reward gains also includes other none money-form, for example, knowledge, fames, compliments from others, etc. Yet another counterexample, people's mood can go up and down chronically and is not encoded in the midbrain dopamine neuron's RPE signal, but it is correlated with people's happiness.

**Note 3**. Ultimately, I proposed that the objective function of life is (1) rather than (3). If someone only sees and optimizes (3), (s)he can easily fall into the trap of consumerism<sup>4</sup>. 




After we set up the objective function, the next thing is how should we optimize it? Researchers have developed many methods to solve the optimal control problem, including Monte Carlo, reinforcement learning, Pontryagin's maximum principle (analytical solutions), etc.
In real life, humans actually intrinsically use a mixture of algorithms that researchers have defined. And the algorithms vary from person to person and from scenario to scenario. Sometimes people adjust their behavior by observing and mimicking previous people's success. (kind of similar to Monte Carlo algorithm) Sometimes people learn through trying by themselves and learn from errors and hits. (kind of similar to reinforcement learning algorithm) Sometimes people analyze the situation and make plans before behaving. (kind of similar to solving the problem analytically).

The optimization problem of life is a normative theory. It only says that people try to pursue the optimal behavior but not necessarily restrict people's behavior to be optimal, aka, it allows suboptimal behavior. For example, a drug addict may choose to have instinct pleasure when using drugs which will result in much more unhappiness during the rest of his/her life. Suboptimal behavior is very common in most of the people as well and people usually call it irrational behavior. For example, someone may be attracted to a fancy advertisement and buys some useless products. After all, what a difficult problem it is to optimize a function throughout ones life span in a very high dimensional space with a lot of uncertainty. None of the current algorithms can find the exact result.


Seeing life as an optimization problem with objective function as (1) or (3) can explain some behavior of many people.

<h3>1. Why should we work? </h3>

It is true that some people can gain happiness in their work. But for most people, it is the salary rather than the happiness during work that sustains their working behavior. People earn money so that after work, they can consume it on things they like and enjoy happiness.

Here I solve a very simplified case of the work-life balance problem in the framework of the optimization problem of life.

Work-life balance problem: Ideally, how many hours should a person spend working, and how many hours should s(he) spend enjoying life?


Assuming there is a person named Alice, he has no other income source besides his salary, which is proportional to his working time, and he feels neither happy nor sad during work. He wants to know the proposition of time he should distribute between working and enjoying life. Here I denote the set of time for work by $\tau_{work}$, the total length of time for work by $T_{work}$, the set of time for enjoying life by $\tau_{nowork}$, and the total length of time for enjoying life by $T_{nowork}$, $T_{work} + T_{nowork} = T_{life}$, $T_{life}$ is the total length of time he can distribute, which is a constant. 


We assume Alice's job can earn $r_{earn}$ dollar per hour, and during nonworking time, Alice's happiness is proportional to the rate of money he spent per hour, $happiness \propto r_{spend} $. In addition, to prevent the money spending rate goes to infinite (in life, this constraint means that he need time to enjoy the food/travel/games that he has bought), we add the constraint that $ r_{spend}(t)< r_{max}, t\in \tau_{nowork}$. Another constraint is that Alice can't spend more money than what he has earned.

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

(4) The more Alice earned per hour (higher $r_{earn}$), the less time he should spend on working.

**Note 4**. This model is overly simplified, and many factors in real life are overlooked. For example, there could be certain period that people can't work (when they are young or old); People may want to leave some money to their offspring instead of consuming them all; The precise number of $r_{max}$ is hard to find, etc.

Although quantitative the model is not accurate, qualitative I do find some people automatically appreciate and practice something similar to this solution. For example, the "work long(hard), play hard" strategy, and the principle of "spending all the money before you die".



<h3>2. Why do parents always supervise their children's behavior?</h3>

There are two things that may make the optimization problem fail to model children's behavior. 

(1) The meaning of happiness for children may change relatively quickly and can't be measured in money form. A newborn baby only knows to eat, drink, seek parents' hug, etc., but as his/her knowledge grows, (s)he starts to find other things that can make him/herself happy. 

(2) The ability of children to solve the optimization problem is usually weaker than adults. For example, they may more relay on the pre-wired biological algorithm to pursue instant satisfaction and have little sightseeing in the future. 
In order to help a child to 1) improve the child's objective function itself, 2) improve the child's optimization algorithm, interference is needed in the early stage of life from a person who has better optimization algorithms. 

Parents behavior can be described using the objective function: 

$$ \int_{birth}^{death} my\ happiness\ dt + \sigma_1 \int_{birth}^{death} child\ 1's\ happiness\ dt + \sigma_2 \int_{birth}^{death} child\ 2's\ happiness\ dt\ + ... \quad \text{(5)}$$

Inside the parent's objective function, children's integrals of happiness are also included. In order to optimize their own objective function in life, parents will exert control to help the children to find a better solution to their lives.

For example, I observe that parents like to force their children to study even if the children don't want to. The behavior of studying may not create big instant happiness (sometimes even very negative feelings). However, it creates much more happiness in their adulthood by providing more choices in careers and, on average, higher salaries. However, not all people in their childhood can realize the benefits and implement this better-optimized behavior. So the job of the parents is to overwrite the children's algorithm, aka be against the children's will and push them to study. 


<h3>Reference:</h3>
[1]. Sutton, R.S. and Barto, A.G., 2018. Reinforcement learning: An introduction. MIT press.<br />
[2]. Schultz, W., Dayan, P. and Montague, P.R., 1997. A neural substrate of prediction and reward. Science, 275(5306), pp.1593-1599.<br />
[3]. Bromberg-Martin, E.S., Matsumoto, M. and Hikosaka, O., 2010. Dopamine in motivational control: rewarding, aversive, and alerting. Neuron, 68(5), pp.815-834.<br />
[4]. https://en.wikipedia.org/wiki/Consumerism<br />
[5]. Binxu and I had an interesting discussion that about persistency: [link](https://animadversio.github.io/personal%20writing/2021/01/15/A-model-of-Persisitency.html)<br />
