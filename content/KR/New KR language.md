+++
title = 'New KR language'
date = 2024-11-18
draft = false
math = true
+++

$\mathcal{EL^\top}$ 
- Limited expression of predicate rules
- allows for constraints
- allows for anonymous objects
- has effective and efficient reasoning methods

$\mathcal{EL^\top}$ Belongs to a bigger family of KR languages knowns as DL's (Description Logics)
Dl's are a category of languages characterized by:
- Clear syntax
- formal unambiguous semantics
The scope of DL's is to provide reasoning, and the main goal is to have decidable reasoning services (sound, complete and terminating algorithms)

Most DL's fall within the two variable fragment of first-order predicate logic (we can only use 2 variables)

First DL was called $\mathcal{AL}$ , which was then extend to $\mathcal{ALC}$

First goal for expansion was to express more, for example
- Quantification (at most three children)
- Inverse relations (HasChild related to HasParent)
- Transitivity (HasAncestor)
At the same time, simplicity is also considered important for Knowledge Bases, as sometimes you don't need a huge amount of data
From this mindset, $\mathcal{EL}$ was born
- $\mathcal{EL}\ only \ \exists \ and \ \sqcap$  
- $\mathcal{FL_0}\ only \ \forall \ and \ \sqcap$ 

## Syntax of $\mathcal{EL^\bot}$
- Concepts are defined by: $C ::= A | \top | \bot | C \sqcap C | \exists r.C$
- Concepts are unary predicates, while rules are binary ones

Examples
- Female
- $\top$
- $\exists hasChild.Female$   individuals with a female son
- $Female \sqcap \exists hasChild.\top$ Female individuals with a child 
- $\exists hasChild.\bot$ is a contradiction

### Semantics
- Concept = Sets
- Role = Pairs
- $\top$ = Tautology
- $\bot$ = Contradiction
- $\sqcap$ = $\wedge$
- $\exists$ is about role successors
- An interpretation is a pair $\mathcal{I} = (\Delta^{\mathcal{I}}, \cdot^{\mathcal{I}})$ where
	- $\Delta^{\mathcal{I}}$ is a non empty set called domain   
	- $\cdot^{\mathcal{I}}$ is the interpretation function which maps every A to a set and every R to a binary relation
The interpretation function is also extended to complex concepts
- $\top^{\mathcal{I}} = \Delta^{\mathcal{I}}$ 
- $\bot^{\mathcal{I}} = \emptyset$
- $(C \sqcap D)^{\mathcal{I}} = C^\mathcal{I} \cap D^\mathcal{I}$   
- $(\exists r.C)^\mathcal{I} = {\delta \in \Delta^\mathcal{I} | \exists \eta \in C^\mathcal{I}.(\delta, \eta) \in r^\mathcal{I}}$  
For Example
- $\Delta^\mathcal{I} = \{\delta, \eta, \theta, \kappa\}$
- $A^\mathcal{I} = \{\theta, \kappa\}$
- $B^\mathcal{I} = \{\delta, \eta, \theta\}$
- $r^\mathcal{I} = \{(\delta, \eta)(\eta, \eta)(\kappa, \kappa)\}$ 
- $s^\mathcal{I} = \{(\delta, \theta)(\eta, \theta)(\kappa, \kappa)\}$ 
then this means that $(\exists s.A)^\mathcal{I} = \{\delta,\eta,\theta\}$ 

## First reasoning problem
A concept C is satisfiable iff there is an interpretation $\mathcal{I}$ such that $C^\mathcal{I} \neq \emptyset$ , this is trivial in $\mathcal{EL}^\mathcal{I}$ 
### Satisfiability
- Every concept name $A \in N_C$ is satisfiable
- $\top$ is satisfiable
- if $C$ is satisfiable, then $\exists r.C$ is satisfiable `C is satisfiable means that there exist some interpretations which make C not empty
- if $C,D$ are satisfiable, then $C \sqcap D$ is satisfiable
### Unsatisfiability
- $\bot$ is unsatisfiable
- if $C$ is unsatisfiable, then $\exists r.C$ is unsatisfiable
- if $C$ is unsatisfiable, then $C \sqcap D$ is unsatisfiable
### Triviality of Satisfiability
Call $\mathcal{EL}$ a subset of $\mathcal{EL}^\bot$ without $\bot$
Any $\mathcal{EL}^\bot$ with $\bot$ as a subconcept is equivalent to $\bot$

To define if a concept is satisfiable or not we just check if $\bot$ is present, if it is, the concept is unsatisfiable

## Concept Subsumption
Let $C$ and $D$ be two $\mathcal{EL}^\bot$ concepts
> C is **subsumed** by D iff in all interpretations $\mathcal{I}$, $C^\mathcal{I} \subseteq D^\mathcal{I}$ 

for example $A \sqcap B \sqcap C \sqsubseteq A \sqcap C$ `everyone which is a male, parent professor is also a male professor
another example is $\exists r.(A\sqcap B)\sqsubseteq \exists r.A\sqcap \exists r.B$ 
`
## Concept Tree
A Concept Tree is a way to graphically represent a concept
- Every $\mathcal{EL}$ concept can be represented via a concept tree
- Nodes are labelled with concept names
- Branches are labelled with role names
- A concept tree is built recursively based on the structure of the concept
---
How to build a concept tree:
- For each top level conjunct X ($\sqcap$):
	- if $X \in N_C$ we label the root with X
	- if X is $\exists r.D$ we crete an r-child of the tree

for example
$B \sqcap \exists r.(A \sqcap B \sqcap \exists s.\top)$  
[[ConceptTreeExample]]

a Homomorphism between 2 concept trees $T_1$ and $T_2$ is a function h: nodes($T_1$) $\rightarrow$ nodes($T_2$) such that: h(root($T_1$)) = root($T_2$) `function which maps the root to the root`
- for every $n \in nodes(T_1), \ label(n) \subseteq label(h(n))$ 
- if m is an r-successor of n, then h(m) is an r-successor of h(n)

$C$ is subsumed by $D$ iff there is a homomorphism from T($D$) to T($C$) **Watch out as subsumption from C to D is present if we can verify an homomorphism from D to C**

an Homomorphic image adds constraints to an object

two concepts C and D are equivalents if
$C \equiv D \\\ if \ C\sqsubseteq D \ and \ D \sqsubseteq C$ 

for example, $\exists r.(\exists s.A \sqcap \bot) \equiv \bot$ 