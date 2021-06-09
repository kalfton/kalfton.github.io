---
layout: post
title: A theory about efficient coding
use_math : true
---

Neurons in the brain respond to external stimuli. In the frame work of efficient coding theory, there is an objective function, and the neuron's response should optimize the objective function.


We can describe the efficient coding problem using the framework of mapping between spaces:

 <p align=center>
<img src="/assets/image_for_notes/efficient_coding_theory/efficient-coding-figure1.png" alt="Input space transformation function" width = "600" align="center">
 <p/>


<p align=center>
	Figure 1
<p/>



The input stimuli lies in a m dimensional space(Input space). For example, if the stimuli are black and white images with m pixels, then each dimension can represents the brightness of each pixel.  <br /> <br />


Then there is a group of neurons, each neuron uses its firing rate to encode objects. The neuron's firing rate is a function on the input space(tuning curve), all the neurons' firing rates in the group form a r dimensional space. (r is the number of neurons) <br /> <br />



If ignoring the noise of neuronal coding, each stimulus evokes a deterministic response in the neuron group, and this forms a map from the input space to the neuron space(transformation function, figure 1). With the assumption that the response of each neuron to the input space is continuous (tuning curve is continuous), We got that the transformation function is continuous.<br /> <br />



Classically the objective function to be optimized is the infomation entropy of the neurons or the mutual information of the maps. 
Given a group of neurons, if they encode the information of the stimuli as much as possible(maximizing the infomation entropy), then people say the neuronal coding is efficient <sup>1,2</sup>. Noted that whether an encoding is efficient no only depends on the encoding map itself, but also depends on the statistics of the external stimuli.<br /> <br />


Another way to descible effient coding is that the neurons firing rate should discriminate more at the place where the objects' appearing probability is more dense, in some scenario it is equivalent to the optimization of information entropy, and in the following I will consider effient coding using this objective function.<br /> <br />


Here I consider a more specific scenario.  I assume 1) the distribution of input stimuli is a multi-variable gaussian distribution, centered at 0. 2) the transformation map is linear, i.e., for every neuron, the turing curve on the inputspace is linear, and thus can be represented as a dot in the dual space of the input space. 3) neuron's turing curve is a random vector, and its representation in the dual space is a multi-variable gaussian distribution centered at zero. if there are m neurons, then each neuron's turing curve a drawing independently from this gaussian distribution.

<p align=center>
<img src="/assets/image_for_notes/efficient_coding_theory/efficient-coding-figure2.png" alt="Input space and its dual space" width = "600" align="center"><br />
<p/>

<p align=center>Figure 2 | an example when dimension = 2<p/>

We use the notation ${\bf X} =  \begin{bmatrix} {\bf x_1} \\ \vdots\\ {\bf x_n} \end{bmatrix} $
to represent the random vector of input stimuli in the input space, $ {\bf W} = \begin{bmatrix} {\bf w_1} \\ \vdots\\ {\bf w_n} \end{bmatrix} $ to represent the random vector of neurons in the dual space. (Bold notation here means random variable)<br /> <br />

<p>
(Relationship of input space and its dual space) Given a neuron represented as $  \left[ \begin{array}{c}  w_1\\ \vdots \\ w_n \end{array} \right] $, then this neuron's tuning curve in the input space is $ n(x_1, ... x_n) = w_1 x_1 + ... + w_n x_n $, i.e., $ w_i = \frac{\partial n}{\partial x_i} $
<p/>



The optimization problem now is to find the gaussian distribution that have the sharpest discrimination, with the firing rate range being constrained. <br /> <br />

Here both the gaussian distribution in the input space and the dual space is center at 0, so their distribution are only determined by the covariance matrix $ C, C_w $ respectively(Figure 2). where $ C = E({\bf XX^T}) $, $ C_w = E({\bf WW^T}) $
I apply the firing rate constraint here as $Var({\bf XW})=E({\bf XWW^T X^T}) = constant$
And the objective function is $ det(C_w) $, $det(C_w) $ describe how wide the gaussian distribution is (propostional to the volume under 95% confidence area, for example)<br /><br />


So the optimization problem can be summarized as:

<h5>Given C, maximizing $det(C_w)$ with the constraint that $Var(XW) = a >0 $ (a is a constant).</h5>



The solution for this problem is that $ C_{w_{opt}} = \frac{a}{n} \bigotimes C^{-1} $.

<h3>Biological meaning</h3>

We sometimes can find this scenario in real experiments. For example: an animal need to view a sequence of images, there are many dimensions here, but we just care about two of them. 1. how bright the images are and 2. How large the images are.
So the pictures lays in this two dimensional space. and experimenters record neurons in an certain brain area, trying to find whether there are neurons responding to either of the object dimension, some neuron only respond to the brightness of the images, some only respond to the size of the images, some neuron respond to both, and some respond to neither. Now the case is that if the two dimensions are correlated in the images, for example, images that are bigger also tends to be brighter, in order to best discriminate the two dimensions, How should the neurons as a propulation tuning to this two dimension? This question can be easily converted to the optimization problem which we previously stated.<br /> <br />


In one experiment<sup>4</sup>, the authors found that locally the neuron's covariance matrix is roughly the inverse of the task variables covariance matrix, and this leads to "whitening operation", which optimize the mutual information.<br /><br />




<h3>Proof of the solution:</h3>

Firstly Let's consider a simple case:
C is an Identity matrix $ C = Id $, what is $ C_{w_{opt}} $?<br /><br />

Because C is an Indentity matrix ,so $ E(x_i* x_j) = 0,  \text{ when }  i \neq j$ and $E(x_i* x_j) = 1 \text{ when } i = j $.<br /><br />

And for constraint:<br />
$$ 
\begin{aligned}
& a = Var({\bf XW}) = E({\bf X W W^T X^T}) \\
& = E({\bf X} C_w {\bf X}) \text{ , (} {\bf W} \text{ and } {\bf X} \text{ are independent)}\\
& = \sum_{i} E(C_w(i, i))\\
& = tr(C_w)
\end{aligned}
$$
<br /><br />

For objective function:<br />
$ C_w $ is a positive definite matrix, so it has n positive eigen values: <br />
$ \sigma_1^2, \sigma_2^2,..., \sigma_n^2 $ <br />
And $ det(C_w) = \sigma_1^2 * \sigma_2^2 * ... * \sigma_n^2 $<br /><br />

from the constraint condition we know:<br />
$ \sigma_1^2 + \sigma_2^2 + ... + \sigma_n^2 = tr(C_w) = a $<br /><br />

By the Arithmetic Mean-Geometric Mean inequality we can get $ det(C_w) <= (a/n)^n $ , and the equality is reached when  $ \sigma_1^2 = \sigma_2^2 = ... = \sigma_n^2 = \frac{a}{n} $<br /><br />

$$ \Rightarrow 
C_{w_{opt}} = 
\begin{bmatrix}
    a/n & 0 & \dots  & 0 \\
    0 & x_{22} & x_{23} & \dots  & 0 \\
    \vdots & \vdots & \ddots & \vdots \\
    0 & 0 & \dots  & a/n
\end{bmatrix}
 = \frac{a}{n} \bigotimes Id

$$
<br /><br />

Hence, $ C_{w_{opt}} = \frac{a}{n} C^{-1} $<br /><br />

Secondly, let's consider the general case：<br /><br />

For the input vector with arbitrary gaussian distribution centered at 0, the covariance matrix C is an arbitary positive definit matrix.
We can change the basis of the input space such that the covariance matrix becomes an identity matrix:<br />
A is the change of basis matrix, X is the random vector under old basis, and X' is the random vector under new coordinates
$ {\bf X} = A{\bf X'} $, where $ {\bf X'} \sim N(0, Id) $,  $ C = E({\bf XX^T}) = E(A{\bf X'X'^T}A^T) = AA^T$<br /><br />

The dual space's basis should change accordingly.<sup>5 </sup> <br />

I denote $ {\bf W } $ as the random vector under old dual basis, $ {\bf W'}$ as the random vector under new dual basis, then we have:
$ {\bf W} = (A^{-1})^T {\bf W'} $<br /><br />

In the new basis, I have proved that the solution of the optimization problem is $ C'_ {W_opt} = E({\bf W'W'^T}) = \frac{a}{n} \bigotimes Id $. Easy to see that the solution of the optimization problem under old basis is the same<br /><br />


$$
\begin{aligned}
C_{w_{opt}} & =  E({\bf WW^T}) = E((A^{-1})^T {\bf W' W'^T} (A^{-1}))\\
& =  (A^{-1})^T (\frac{a}{n} \bigotimes Id) A^{-1}\\
& = \frac{a}{n} \bigotimes (A^{-1})^T A^{-1}\\
& = \frac{a}{n} \bigotimes (A A^T)^-1\\
& = \frac{a}{n} \bigotimes C^{-1}\\
\end{aligned}
$$


Thus we have $ C_{w_{opt}} = \frac{a}{n} \bigotimes C^{-1} $<br/><br />



<h3>Open discussion:</h3>
We can consider a more general efficient coding problem. The object space is can be an arbitary manifold X, and the objects has a given probability distribution on the manifold with probabliity density function $ f_X $. An neuron's tuning curve is a smooth function on the manifold. Each neuron's tuning curve is drawn independently from a set of functions(function space) with a certain probability distribution on the function space. We want to know what is the probability distribution on the function space that can maximize certain objective function.<br /><br />

An example objective function could be 
$$ E_{w \in W}(\int_X |dw| f_X d \sigma) $$ 





<h3>Reference:</h3>
[1]. Barlow, H.B., 1961. Possible principles underlying the transformation of sensory messages. Sensory communication, 1(01).<br />
[2]. Simoncelli, E.P. and Olshausen, B.A., 2001. Natural image statistics and neural representation. Annual review of neuroscience, 24(1), pp.1193-1216.<br />
[3]. Park, I.M. and Pillow, J.W., 2017. Bayesian efficient coding. BioRxiv, p.178418.<br />
[4]. Koay, S.A., Thiberge, S.Y., Brody, C.D. and Tank, D.W., 2019. Sequential and efficient neural-population coding of complex task information. bioRxiv, p.801654.<br />
[5]. https://math.stackexchange.com/questions/950290/help-on-the-relationship-of-a-basis-and-a-dual-basis<br />
[6]. https://en.wikipedia.org/wiki/Harmonic_map <br />


%% to do
1. Formating the equations
2. Write some discussions about further direction, opening questions, and biological interpretation
3. Make figures (first find out how many figures do you need?)