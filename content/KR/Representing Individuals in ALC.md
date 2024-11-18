+++
title = 'Representing Individuals in ALC'
date = 2024-11-18
draft = false
math = true
+++
## ABoxes
Consider an infinite set $N_I$ of individual names, disjoint with $N_C \ \mbox{and} \ N_R$ 

An **Assertion** is an expression of the form 
- $C(a)$ where $a \in N_I$ and C is an $\mathcal{ALC}$ concept
- $r(a,b)$ where $a,b \in N_I$ and $r \in N_R$

An assertion box `ABox` is a finite set of assertions

this concepts is kinda similar to relational database $\to$ keep in mind that usually DB's are complete (if a person isn't in the student's DB, he's not a student ), while ABoxes aren't and work with an **Open World Assumption**

The interpretation function $\cdot^{\mathcal{I}}$ maps each $a \in N_I$ to an element $a^\mathcal{I} \in \Delta^\mathcal{I}$ 

when does the interpretation satisfy my knowledge?
$\mathcal{I}$ satisfies the assertion
- C(a) iff $a^\mathcal{I} \in C^{\mathcal{I}}$ 
- r(a, b) iff $(a^\mathcal{I}, b^{\mathcal{I}}) \in r^\mathcal{I}$ 
$\mathcal{I}$ is a model of the ABox $\mathcal{A}$ if it satisfies all assertions in $\mathcal{A}$

A KB is consistent iff it has a model
we decide consistency by applying the tableau algorithm to a large initial set of assertions

To make our algorithm more efficient we divide the problem into simpler cases

 Example, checking consistency between a TBox $\mathcal{T}$ and an ABox $\mathcal{A}$

![[Lesson 1412.jpeg]]
How do we apply the tableaux algorithm?
## Root Pre-completion and expansion
- Pre-completion: we apply all non generating rules (not $\exists$) until saturation
- Expansion: we apply the full tableaux to each pre-completed individual one at a time
The KB ($\mathcal{T, A}$) is consistent iff the tableau algorithm produces a saturated and open ABox.

The tableau algorithm, when successful, generates a forest-lie model `lots o' trees` with:
- A root system arbitrarily interconnected (ABox)
- Trees gorging from each element
![[forest model]]
`incredible drawing by rafael`


Nominals $\mathcal{O}$
A nominal is a concept with exactly one element
`the president of the USA` 
syntax: $\{a\}; a \in N_I$ 
Examples:
- $EUCountry \sqsubseteq \{austria\} \sqcup \{belgium\} \sqcup . . . \sqcup \{sweden\}$  
- $French \sqsubseteq \exists hasPresident.\{macron\}$ `if someone is french they have a oresudet which is macron`


## Cardinality Constraints $\mathcal{Q, N}$  
A cardinality constraint limits the number of successors of an object
syntax; $\geq n r.C; n \in \mathbb{N},r \in N_R, \ C \ a \ concept$
Examples:
- $\{bai\} \sqsubseteq \neg(\geq 181hasStudent.\top)$


## Inverse roles $\mathcal{I}$
Inverse roles allow to traverse role relations backwards
syntax:$r^-, r \in N_R$
Examples:
- $Male\sqcap \exists hasChild^-.\top \sqsubseteq Son$ 
- $\top \sqsubseteq \neg(\geq 3hasChild^-.\top)$ `class of individuals with 3 or more childrens`

## Self
used to describe a property of the object

## Transitivity $\mathcal{S}$

