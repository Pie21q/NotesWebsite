+++
title = 'ALC'
date = 2025-02-20
draft = false
math = true
+++

In $\mathcal{EL}^\bot$ negation can only be partially achieved
The construction $A \sqcap B \sqsubseteq \bot$ Means that no element a can belong to B

$Mortal \sqcap Immortal \sqsubseteq \bot$ Tells us no object can be both Mortal and Immortal at the same time, but we have no way to express an object which is neither Mortal or Immortal, also how can we express the fact that if an object is not Mortal, then it has to be immortal $\neg Mortal \sqsubseteq Immortal$ 

This is not allowed in $\mathcal{EL}^\bot \rightarrow$ we need a new language $\rightarrow \mathcal{ALC}$  

$\mathcal{ALC}$ is an extension of $\mathcal{EL}^\bot$ which allows support for negation
	$C ::= A \ | \ \top \ | \ C \sqcap C \ | \ \exists r.C \ | \ \neg C$ 

we also add $\forall$ to our language
	$\forall r.C := \neg(\exists r.\neg C)$ 

Every $\mathcal{ALC}$ concept can be rewritten in NNF, considering the same rules we already know from Computational Logic (No implications this time :] )

- Also in case of quantifiers
	- $\neg (\forall r.C) := \exists r.\neg C$ 
	- $\neg (\exists r.C) := \forall r.\neg C$

To check for consistency of an object $C$ in $\mathcal{ALC}$ we want to build an object which belongs to it through a Tableaux algorithm 

- we start with initialization $\rightarrow \ assert \ C(a)$ 
- We then proceed with decomposition, applying the tableaux rules
	- $\sqcap$ | if $C \sqcap D \in \mathcal{A}$  then add $C(x), D(x)$ to $\mathcal{A}$
	- $\sqcup$ | if $C \sqcup D \in \mathcal{A}$  then add either $C(x) \ or \ D(x)$ to $\mathcal{A}$
	- $\exists$ | if $\exists r.C(x) \in \mathcal{A}$  then add $r(x, y), C(y)$ to $\mathcal{A}$
	- $\forall$ | if $r(x, y), \forall r.C(x) \in \mathcal{A}$  then add $C(y)$ to $\mathcal{A}$

There is no rule for handling negation $\rightarrow$ it's the last item in the decomposition and it plays a role in deciding the existence of a satisfying interpretation

a set of assertions $\mathcal{A}$ can be:
- saturated, if no rule is applicable to it
- closed, if $\{A(a), \neg A(a) \} \subseteq \mathcal{A}$ for some $A \in N_C$ 
- open, if it's not closed 

A concept $C$ is satisfiable if the tableaux algorithm yields a saturated and open set of assertions

## What if we're working with TBoxes
We add a new rule to the tableaux
$\sqsubseteq$ | if $C \sqsubseteq D \in \mathcal{T}$ and  x appears in $\mathcal{A}$, add $\neg C \sqcup D(x)$ to $\mathcal{A}$ 
We first have to transform our TBox to NNF 

The new rule we added doesn't add simpler concepts $\rightarrow$ the process goes on indefinitely

all the nodes are the same, once we recognize the pattern w edo not need further enumeration


## Adding individuals to $\mathcal{ALC}$ 

### Example
We wanna make sure that if `HasChild(rafael, joe)` , then `rafael` is a parent
We need to add this to the Knowledge Base $\rightarrow$ these informations form the assertional Knowledge of the domain

considering a set $N_I$ of individual names
an assertion is an expression of the form
- $C(a)$ where $a \in N_I$ and $C$ is an $\mathcal{ALC}$ concept
- $r(a, b)$ where $a, b \in N_I$ and $r \in N_r$ 
An ABox is a finite set of assertions
A Knowledge Base is a pair $\mathcal{K} = (\mathcal{T,A})$ 

A KB is consistent iff it has a model

To check for this we can apply our tableaux algorithm to the KB 
1) **pre-completion**: we apply all non-generating rules ($\not \exists$) until saturation
2) **expansion**: we apply tableaux rules to each pre-completed individual

Our KB is consistent if the tableaux algorithm produces an open and saturated ABox 

When successful, the tableaux algorithm generates a forest-like model 


To check if a subsumption holds we take the right part, invert it and move it to the left with a $\sqcap$, we then try and build a model to test for satisfiability
- Unsat, Holds
- Sat, doens't Hold


## Exercises
- To check for satisfiability we look for $\bot$ , then for $\sqcup$ and try to build a model even with $\bot$ present
- To check for TBox consistency we first transform the GCI's in normal form, then we try to construct a model 
- To check if a concept $\psi$ is satisfiable with respect to an $\mathcal{ALC}$ TBox we simply add it as if it was a formula $\top \sqsubseteq \psi$ , then check for SAT
- To check if a subsumption of the kind $\phi \sqsubseteq \gamma$ holds with respect to an $\mathcal{ALC}$ TBox we transform it into $\phi \sqcap \neg \gamma$ and check for SAT 