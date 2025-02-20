+++
title = 'Temporal Logic'
date = 2025-02-20
draft = false
math = true
+++


All the languages we studied before are static, we need a way to handle time
In our case we will use $LTL_f$ , a temporal logic with:
- discrete time
- linear evolution
- considering only the future
- finite, unbounded time

$LTL_f$ is an extension of propositional logic which adds the operators $\bigcirc$ `next` and $\mathcal{U}$   `until` 

$LTL_f$ formulas re built using the grammar rule stated below
$\varphi ::= x \ | \ \neg \varphi \ | \ \varphi \wedge \varphi \ | \ \bigcirc \varphi \ | \ \varphi \mathcal{U} \varphi$ 

keep in mind that:
- $\bigcirc \varphi$ means $\varphi$ is true in the next point in time
- $\varphi \mathcal{U} \psi$ means $\varphi$ is true until $\psi$ becomes true

How can we check for satisfiability?

We can develop a tableaux like structure
- $\varphi$ is always satisfied at the first timepoint
- at the last timepoint, no formula $\bigcirc \psi$ is satisfied
- at a timepoint n, a formula $\psi$ is satisfied if a formula $\neg \psi$ is not satisfied
- $\bigcirc \psi$ is satisfied at a timepoint n iff $\psi$ is satisfied at a timepoint n + 1
- $\psi_1 \mathcal{U} \psi_2$ is satisfied at a timepoint n iff $\psi_2$ or $\psi_1 \wedge \bigcirc \psi_1 \mathcal{U} \psi_2$ is satisfied at timepoint n

We can divide a formula $\varphi$ into a set of sub formulas $sub(\varphi)$ like this:

$\varphi := (\bigcirc x)\mathcal{U} \neg y$ 

sub($\varphi$):
- $(\bigcirc x)\mathcal{U} \neg y$ $
- $\bigcirc x$
- $x$
- $\neg y$
- $y$

we can also describe a closure of this set
- $\neg((\bigcirc x)\mathcal{U} \neg y)$ $
- $\neg \bigcirc x$
- $\neg x$
- $\bigcirc((\bigcirc x)\mathcal{U} \neg y)$
- $\neg \bigcirc((\bigcirc x)\mathcal{U} \neg y)$

A type is a maximally consistent set of csub, and every time defines exactly one valuation

## Type Graphs
The type graph $G_\varphi$ is the directed graph of $\varphi$ such that:
- the nodes of $G_\varphi$ are the types of $\varphi$
- there is an edge from $\mathcal{T_1}$ to $\mathcal{T_2}$ iff for very $\bigcirc \psi \in$ csub$(\varphi)$ 

The paths in the graph describe a valid behaviour in the temporal model, to describe a temporal model we need 2 more conditions
- the path should start with a type containing $\varphi$
- the path should end without a $\bigcirc$ hanging

A type $\mathcal{T}$ can be
- initial if $\varphi \in \mathcal{T}$ (it needs to have the original formula)
- final if it contains no formula of the form $\bigcirc \psi$

An $LTL_f$ is satisfiable iff there is a path from an initial type to a final type in $G_\varphi$


$LTL_f$ can be expanded with the logic $\mathcal{ALC}_{LTL_f}$ , by adding evolving interpretations
A temporal interpretation becomes then a finite sequence of $\mathcal{ALC}$ interpretations


## Exercises
- To compute the csub we divide the formula into sub formulas then add the negation, + for every until we add the next of the until and the negation of it
	- $\varphi := \bigcirc x, \ csub(\varphi) = \{\bigcirc x, \neg \bigcirc x, x, \neg x \}$  
- to get a type we need to choose for every sub formula either the positive or negated one, making sure to keep consistency
	- $\tau_1 = \{ \bigcirc x, x \}$ 

	- An initial type must contain the original formula
	- A final type mustn't contain any formula of the type $\bigcirc x$ (there is no next point in time)
- To check if 2 types are connected through an edge we must check if the $\bigcirc x$ in $\tau_1$ are respected in $\tau_2$ 
	- $\tau_1 = \{\bigcirc x, \neg x\}$ 
	- $\tau_2 = \{\bigcirc x, x\}$  The next statement is respected as in the next timeframe $x$ is positive $\rightarrow$ the 2 types are connected through an edge

a formula $\varphi$ is satisfiable if there is an edge from an initial type to a final one, a formula $\neg \varphi$ has the same graph as $\varphi$ but all the types that weren't initial become initial, while the final types stay the same

$\Omega \mathcal{U} \Gamma$ 
- Omega has to be true until $\Gamma$ is true


$\lozenge x := \top \mathcal{U} x$ eventually x is going to be true
$\square x := \neg \lozenge \neg x$ always x