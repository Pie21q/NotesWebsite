+++
title = 'EL'
date = 2025-02-20
draft = false
math = true
+++


# $\mathcal{EL}$
- An $\mathcal{EL}$ GCI is an expression of the form $C \sqsubseteq D$ with $C \ and \ D$ being $\mathcal{EL}$ concepts
- A $\mathcal{EL}$ TBox is a finite set of GCI's

A Concept $C$ is satisfiable iff $C \not \sqsubseteq \bot$ 

In the presence of TBoxes we cannot use homomorphism to check for subsumption $\rightarrow$ GCI's add objects to the concept tree and we would end up with infinite constructions

## New method based on consequence propagation
`We combine to GCi's to produce a new one`

first we simplify our GCI in normal form
- Normal Form GCI's:
	- $A \sqsubseteq B$
	- $A_1 \sqcap A_2 \sqsubseteq B$
	- $A \sqsubseteq \exists r.B$
	- $\exists r.A \sqsubseteq B$
Normal Form GCI's can be seen as existential rules with constraints
$\exists r.A \sqsubseteq B \rightsquigarrow B(x) \leftarrow r(x, y), A(y)$ 

$\top$ in the body and $\bot$ in the head are removed
$\exists HasChild.\top \sqsubseteq Parent \rightsquigarrow Parent(x) \leftarrow HasChild(x, y)$ 
$Mammal \sqcap Reptile \sqsubseteq \bot \rightsquigarrow \ \ \  \leftarrow Mammal(x), Reptile(x)$ 

Normalisation Doesn't affect subsumption relations and $norm(\mathcal{T})$ is a conservative extension of $\mathcal{T}$, meaning to check for subsumption it is sufficient to check for TBoxes in normal 


Keep in mind that any Formula with $\bot$ is unsatisfiable and equal to $\emptyset$ and that
- $\emptyset \sqsubseteq \emptyset \rightsquigarrow$ True
- $\emptyset \sqsubseteq Formula \rightsquigarrow$ True
- $Formula \sqsubseteq \emptyset \rightsquigarrow$ False


## Exercises 

- To check for satisfiability of a concept we just look for the absence of $\bot$ from it
- To check for subsumption relationships we still check for $\bot$
	- If $\bot$ is present the entire formula becomes unsatisfiable and we follow these rules
		- $\bot \sqsubseteq \bot$ True
		- $\bot \sqsubseteq \ formula$ True
		- $formula \sqsubseteq \bot$ False

- To construct a model of a TBox we first transform to normal form, then represent the TBox (Transformation may not be necessary)

if you get a TBox and need to check if some consequences holds
- Compute Completion algorithm of the TBox
- Transform the consequences into normal form
- Add the new variables to the Completion Algorithm
- Check for consequences

