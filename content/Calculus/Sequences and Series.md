
+++
title = 'Sequences and Series'
date = 2024-12-19
draft = false
math = true
+++

list of numbers written in a specific order

$\lim_{n \to \infty} a_n = L$ `the value of the series approaches L as n approaches infinity`

We can find the limit of a series just by treating it as the limit of a function

## Convergent and Divergent Series
- If the sequence of partial sums is convergent (has finite limits), then we can refer to the series as convergent and if $\lim_{n \to \infty} s_n = s, then \ \sum^\infty_{i=1}a_i = s$ .
- If the sequence of partial sums is divergent (limit doesn't exist or goes to $\pm \infty$), then the series is also called divergent

To define convergence we can just compute the limit of the general formula of a series: This can prove to be quite difficult, as finding the general formula can be pretty hard

To more easily find the convergence of a series, we can make use of some test

## Comparison Test
given the series $\sum a_n$ and $\sum b_n$ with $a_n,b_n \geq 0 \forall n \ and \ a_n \leq b_n \forall n$ then
- if $\sum b_n$ is convergent, then so is $\sum a_n$ 
- if $\sum a_n$ is divergent, then so is $\sum b_n$ 


## Ratio Test

given the series $\sum a_n$ , we define $L= \lim_{n \to \infty} |\frac{a_{n+1}}{a_n}|$  , we can then find $a_{n+1}$ by substituting n with n+1 and compute the limit in order to find L.
- if L < 1 the series is absolutely convergent
- if L > 1 he series is divergent
- if L = 1 the series may be divergent, conditionally convergent or absolutely convergent

## Root Test

given the series $\sum a_n$, we define $L = \lim_{n \to \infty} \sqrt[n]{|a_n|} =\lim_{n \to \infty} |a_n|^{\frac{1}{n}}$ 
after computing the limit and finding L
- if L < 1 the series is absolutely convergent
- if L > 1 he series is divergent
- if L = 1 the series may be divergent, conditionally convergent or absolutely convergent
keep in mind that $\lim_{n \to \infty} n^{\frac{1}{n}} = 1$ 

Permanence of sign for sequences
1) if $a_n \to l$ and $a_n \geq 0 \ \forall n$ then $l \geq 0$ 
2) if $l > 0$  and $a_n \to l$ then $\exists n_0 \ s.t.\ \forall n \geq n_0, a_n > 0$ 
Proof:
1) The limit $l$ can't be $< 0$, otherwise $\exists \mathcal{E} \ s.t. \ I_{\mathcal{E}}(l)$ and such neighbor doesn't contain any of the $a_n$, so $l$ cannot be the limit, thus $l \geq 0$ 
2) considering $\mathcal{E} = \frac{l}{2}$, Then, since $l$ is limit of $a_n$, $\exists n_0 \ s.t. \ \forall n \geq n_0, a_n \in I_\mathcal{E} (l)$. But $I_\mathcal{E}(l) \ c (0, + \infty)$ so $a_n >0 \ \forall n \geq n_0$   