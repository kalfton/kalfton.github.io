---
layout: post
title: Derivation of TAP Equation
use_math : true
published: true
date:  Jan. 1, 2026
author: Kaining Zhang
tags: [academic, math]
---
Here I derive the TAP equation directly from calculating the free energy (or the log of partition function).

The free energy of the SK model $f_{\mathrm{TAP}}$ comprises two parts: the energy term and the entropy term.

**The energy term:**

$$
E(\beta,\mathbf{m})=\left\langle -\frac{1}{2} \sum_{i \neq j}J_{ij}\sigma_i\sigma_j-\; \sum_{i}h_i\sigma_i\right\rangle
= -\frac{1}{2} \sum_{i \neq j}J_{ij} J_{ij}\langle\sigma_i\sigma_j\rangle - \sum_{i} h_i m_i,
\quad \text{Eq. 1}
$$

Here $m_i=\langle\sigma_i\rangle$, and $\langle *\rangle$ denotes the average over the Boltzmann distribution of $\{\sigma_i\}$.

We will calculate $\langle\sigma_i\sigma_j\rangle$ explicitly as a function of $\beta$ and $\mathbf{m}$: 

The state of $\sigma_j$ can affect the state of $\sigma_i$:

$$
\delta_j \sigma_i \;\triangleq\; \langle\sigma_i\rangle^{(\sigma_j=-1)}-\langle\sigma_i\rangle^{(\sigma_j=+1)}.
$$

We can write $\langle\sigma_i\rangle^{(\sigma_j=-1)}$ and $\langle\sigma_i\rangle^{(\sigma_j=+1)}$ explicitly:

$$
\langle\sigma_i\rangle^{(\sigma_j=+1)} = \delta_j\sigma_i \cdot P(\sigma_j=-1) + m_i,
\quad \text{Eq. 2}
$$

$$
\langle\sigma_i\rangle^{(\sigma_j=-1)} = -\delta_j\sigma_i \cdot P(\sigma_j=+1) + m_i,
\quad \text{Eq. 3}
$$

Where $P(\sigma_j=-1)=\frac{1-m_j}{2}$ and $P(\sigma_j=+1)=\frac{1+m_j}{2}$, are the marginal probability of $\sigma_j=-1$ or $+1$, Then we have:

$$
\langle\sigma_i\sigma_j\rangle-\langle\sigma_i\rangle\langle\sigma_j\rangle
\approx 1\cdot \langle\sigma_i\rangle^{(\sigma_j=+1)}\cdot P(\sigma_j=+1) +(-1)\cdot \langle\sigma_i\rangle^{(\sigma_j=-1)}\cdot P(\sigma_j=-1)-m_i m_j$$

$$
=2\cdot \delta_j\sigma_i\cdot P(\sigma_j=-1)P(\sigma_j=+1)
=\frac{1}{2}\delta_j\sigma_i\cdot(1-m_j^2),
\quad \text{Eq. 4}
$$

Now we need to estimate $\delta_j\sigma_i$.  We know that:

$$
m_i=\langle\sigma_i\rangle=\left\langle \tanh\big(\beta\langle J_{ij}\sigma_j + h_i\rangle\big)\right\rangle
$$

So, with $x_i \triangleq\ J_{ij}\sigma_j+h_i$:

$$
\delta_j\sigma_i \approx 
\frac{\partial\langle\sigma_i\rangle}{\partial\sigma_j}\cdot(1-(-1))
= 2\cdot\frac{\partial\langle\sigma_i\rangle}{\partial x_i}\cdot\frac{\partial x_i}{\partial\sigma_j}
$$

The susceptibility $\frac{\partial\langle\sigma_i\rangle}{\partial x_i}=\beta(1-m_i^2)$, and $\frac{\partial x_i}{\partial\sigma_j}=J_{ij}$, thus we have:

$$
\delta_j\sigma_i = 2\beta(1-m_i^2)J_{ij},
\quad \text{Eq. 5}
$$

Substitute Eq.5 into Eq. 4:

We have:

$$
\langle\sigma_i\sigma_j\rangle-\langle\sigma_i\rangle\langle\sigma_j\rangle
=\beta(1-m_i^2)J_{ij}(1-m_j^2)
$$

Aka:

$$
\langle\sigma_i\sigma_j\rangle=\beta(1-m_i^2)J_{ij}(1-m_j^2)+m_i m_j,
\quad \text{Eq. 6}
$$

Now we can substitute Eq. 6 into Eq 1 and get:

$$
E(\beta,\mathbf{m})
= -\sum_{i \neq j}\frac{1}{2}J_{ij}m_i m_j - \sum_{i}h_i m_i
-\frac{\beta}{2} \sum_{i \neq j} (1-m_i^2)J_{ij}^2(1-m_j^2),
\quad \text{Eq. 7}
$$

**The Entropy term ($\beta=0$):**

When $\beta=0$, The Entropy term can be calculated directly as the information entropy assuming units state are independent from each other:

$$
S(\beta=0,\mathbf{m})
=-\frac{1}{2}\sum_i\left[
(1+m_i)\log\left(\frac{1+m_i}{2}\right)
+(1-m_i)\log\left(\frac{1-m_i}{2}\right)
\right]
$$

The log of the partition function, $\beta f_{\mathrm{TAP}}$, when $\beta=0$, equals the negative of the entropy

$$
\beta f_{\mathrm{TAP}}(\beta=0,\mathbf{m})=-S(\beta=0,\mathbf{m}),
\quad \text{Eq. 8}
$$


**The free energy when $\beta \neq 0$:**

To derive the partition function when $\beta\neq 0$, we need to take advantage of the definition of energy in terms of the partition function:

$$
E=\frac{\partial(\ln Z)}{\partial\beta}=\frac{\partial(\beta f_{\mathrm{TAP}})}{\partial\beta}
$$

Thus we can integrate the energy $E$ on $\beta$ to get the free energy at non zero $\beta$:

$$
\beta f_{\mathrm{TAP}}(\beta,\mathbf{m})
=\beta f_{\mathrm{TAP}}(\beta=0,\mathbf{m})+\int_0^\beta E(\beta',\mathbf{m})\,d\beta',
\quad \text{Eq. 9}
$$

Substitute Eq. 7 and Eq. 8 into Eq.9 and perform the integration:

$$
\beta f_{\mathrm{TAP}}(\beta,\mathbf{m})
= -\frac{\beta}{2}\sum_{i \neq j}J_{ij}m_i m_j - \beta \sum_{i} h_i m_i
-\frac{\beta^2}{4}\sum_{i \neq j}(1-m_i^2)J_{ij}^2(1-m_j^2)
$$

$$+\frac{1}{2}\sum_i\left[
(1+m_i)\log\left(\frac{1+m_i}{2}\right)
+(1-m_i)\log\left(\frac{1-m_i}{2}\right)
\right]
$$

Aka, the free energy is:

$$
f_{\mathrm{TAP}}(\beta,\mathbf{m})
= -\frac{1}{2}\sum_{i \neq j}J_{ij}m_i m_j - \sum_{i}h_i m_i
-\frac{\beta}{4}\sum_{i \neq j}(1-m_i^2)J_{ij}^2(1-m_j^2)
$$

$$
+\frac{1}{2\beta}\sum_i\left[
(1+m_i)\log\left(\frac{1+m_i}{2}\right)
+(1-m_i)\log\left(\frac{1-m_i}{2}\right)
\right],
\quad \text{Eq. 10}
$$

The TAP equation and be derived by finding the maximal of $f_{\mathrm{TAP}}(\beta,\mathbf{m})$ in the magnetization space, aka $\frac{\partial f_{\mathrm{TAP}}(\beta,\mathbf{m})}{\partial m_i}=0$, for all $i$:

$$
-J_{ij}m_j - h_i + \beta J_{ij}^2(1-m_j^2)m_i
+ \frac{1}{2\beta}\log\left(\frac{1+m_i}{1-m_i}\right)=0
$$

Aka:

$$
m_i = \tanh\left(\beta\left[J_{ij}m_j + h_i - \beta J_{ij}^2(1-m_j^2)m_i\right]\right),
\quad \text{Eq. 11}
$$

This is the TAP equation with the Onsager reaction field.

**Reference:**

Nishimori, Hidetoshi. Statistical physics of spin glasses and information processing: an introduction. No. 111. Clarendon Press, 2001.

