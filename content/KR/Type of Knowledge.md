+++
title = 'Type of Knowledge'
date = 2024-11-18
draft = false
math = true
+++

With all languages seen so far, knowledge is considered **Static**
This is meaningful in many domains, but insufficient in the context of processes 

We need a way to deal with time and dynamic knowledge

## Time
To deal with time we first have to decide if it's 
- **discrete** or **continuous**
- **linear** or **branching**

we will deal with time using $LTL_f$ (showcases the main ideas of temporal reasoning while still remaining pretty simple)

 $LTL_f$ is a temporal logic with:
 - Discrete time `we look at "snapshots" of time`
 - linear evolution
 - considers only the future
$LTL_f$ extends propositional logic with 'next' ($\bigcirc$) and 'until' ($\mathcal{U}$) operators

$LTL_f$ formulas are built through the grammar rule
$$\varphi ::= x | \ \neg \varphi\ | \ \varphi \wedge \varphi\ | \bigcirc \varphi \ |\ \varphi \mathcal{U} \varphi $$
- $\bigcirc \varphi$ : in the next point in time, $\varphi$ is true
- $\varphi \mathcal{U} \psi$ : $\varphi$ is true until $\psi$ becomes true  

To interpret $LTL_f$ formulas, we consider a finite sequence of timepoints {0, 1, . . . ., n} and, for each timepoint, a propositional valuation

A temporal model is a finite sequence $M = V_0, .....,V_n$ of propositional valuations where n is the length of the temporal model M

if M is a temporal model of length n and $0 \leq k \leq n$ 
- $M, k \vDash x \ \mbox{iff} \ V_k \vDash x$  `M satisfies x at time k`
- $M, k \vDash \neg \varphi \ \mbox{iff} \ M,k \ \nvDash \varphi$ 
- $M,k \vDash \varphi \wedge \psi \ \mbox{iff} \ k < n \ \mbox{and} \ M,k+1 \vDash \varphi$ 
- $M,k \vDash \bigcirc \varphi \ \mbox{iff} \ k <n \ \mbox{and} \ M,k+1 \vDash \varphi$  `if the next point in time is true, the previous one also is`
- $M,k \vDash \varphi \mathcal{U} \psi \ \mbox{iff} \ \exists l, k \leq l \leq n \ \mbox{s.t.} \ M,l \vDash \psi \ \mbox{and for all} \ j,k \leq j \leq l, \ M, j \vDash \varphi$  

Example

![[Lesson 1413.jpeg]]



The temporal model M satisfies $\varphi$ iff $M,0 \vDash \varphi$ 
The formula $\varphi$ is satisfiable iff there's a temporal model which satisfies it