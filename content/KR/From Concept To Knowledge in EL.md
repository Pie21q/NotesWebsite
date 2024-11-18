+++
title = 'From Concept to knowledge'
date = 2024-11-18
draft = false
math = true
+++
so far we described concepts and their relationships

How do we express knowledge?
- Trough constraints on the relevant interpretations (Tbox)

A Tbox (terminological Box) is used to impose restrictions on the potential interpretation of concepts

A ($\mathcal{EL}^\bot$) general concept inclusion `GCI` is an expression $C \sqsubseteq D$ with C and D $\mathcal{EL}^\bot$ concepts
a TBox is a finite set of GCI's

an interpretation $\mathcal{I}$ satisfies the GCI  $C \sqsubseteq D$ iff $C^{\mathcal{I}} \subseteq D^\mathcal{I}$ 

$\mathcal{I}$ is a model of the TBox $\mathcal{T}$ is it satisfies all of the GCI's in T
for example
$A \sqsubseteq \exists r.B$ 

in the presence of a tbox, reasoning is restricted to the class of models only
- Concept satisfiability: is there a model I of T such that $C^\mathcal{I} \neq \emptyset$ 
- Concept subsumption: does $C^\mathcal{I} \subseteq D^\mathcal{I}$  hold for all models  $\mathcal{I}$ of $\mathcal{T}$
- TBox consistency: Does $\mathcal{T}$ have a model?

Keep in mind that concepts may be unsatisfiable `w.r.t. consistent TBoxes`
$A \sqsubseteq \exists r.(A \sqcap B) \ \ \ \ A \sqcap B \sqsubseteq \bot$ 

$\mathcal{T}$ has a trivial model but A is unsatisfiable
>$\Delta^\mathcal{I} = {\delta}$ 
>$A^\mathcal{I} = B^\mathcal{I} = \emptyset$ 
>$r^\mathcal{I} = \emptyset$ 

>$(A\sqcap B)^\mathcal{I}$ = $A^\mathcal{I} \wedge B^\mathcal{I} = \emptyset \subseteq \emptyset$ 

$T \sqsubseteq A, \ A \sqsubseteq \bot$ is inconsistent

C is subsumed by D iff for every model $\mathcal{I}, \ C^\mathcal{I} \subseteq D^\mathcal{I}$, meaning is not subsumed by D iff $\exists \mathcal{I} s.t. C^\mathcal{I} \not\subseteq D^\mathcal{I}$ 
$\top$ is not subsumed by $\bot$ iff there exists a model $\mathcal{I}$ such that $\Delta^\mathcal{I} = \top^\mathcal{I} \not = \emptyset = \bot^\mathcal{I}$

A concept is satisfiable iff C is not subsumed by $\bot \rightarrow$ we focus on subsumption

## Simplification without $\bot$
an $\mathcal{EL}$ toolbox is an $\mathcal{EL}^\bot$ TBox without $\bot$
- **Every $\mathcal{EL}$ TBox is consistent `as bottom isn't present`**
	- we can always build an interpretation $A^\mathcal{I} = \{\delta\}$ with $r^\mathcal{I} = \{(\delta, \delta) \}$ 
	- Every $\mathcal{EL}$ concept is satisfiable w.r.t an $\mathcal{EL}$ TBox

## Deciding Subsumption
Homomorphism approach doesn't necessarily work in the case of TBoxes
- GCI's add objects to concept trees
- How do we avoid building an infinite tree?
We need a new algorithm based on consequence propagation $\rightarrow$ we combine 2 GCI's to derive a new one 

## A GCI is called normal form if it has one of these shapes
$A \sqsubseteq B$
$A_1 \sqcap A_2 \sqsubseteq B$
$A \sqsubseteq \exists r.B$
$\exists r.A \sqsubseteq B$ 

**A normal form GCI has at most one constructor and no conjunction in the right**
A TBox is in normal form if all GCI's contained are in normal form

For example
- $Person \sqsubseteq \exists hasParent.Person$
- $Mammal \sqcap Oviparous \sqsubseteq Monotreme$

GCI's in normal form are existential rules with constraints
- $A \sqsubseteq B \rightsquigarrow B(x) \leftarrow A(x)$ 
- $A_1 \sqcap A_2 \sqsubseteq \rightsquigarrow B(x) \leftarrow A_1(x), A_2(x)$ 
- $A \sqsubseteq \exists r.B$  `A must have an r successor (y) which belongs to B` $\rightsquigarrow r(x,y), B(y) \leftarrow A(x)$ `this is problematic as there are 2 predicates in the head` we write it with a new predicate such as $S_{b,r} (x,y) \leftarrow A(x)$  with $r(x,y) \leftarrow s_{r,b}(x,y) \ and \ B(y) \leftarrow S_{b,r}(x,y)$ 

$Parent \sqsubseteq \exists hasChild.\top \rightsquigarrow hasChild(x,y) \leftarrow Parent(x)$ `in this case we do not need the previous construction as we dont care about the properties of the child`

$Mammal \sqcap Reptile \sqsubseteq \bot \rightsquigarrow \ \leftarrow Mammal(x), Reptile(x)$   this GCI is a constraint, as an object cant be both a Mammal and a Reptile

Every TBox can be transformed into normal form just by applying normalisation rules
$Normalisation \not = Restriction$
$\hat{C}, \hat{D}$ are complex concepts, A is a new concept name
- $\hat{C} \sqsubseteq \hat{D} \rightsquigarrow \hat{C} \sqsubseteq A, A \sqsubseteq \hat{C}$ 
- $B \sqsubseteq C \sqcap D \rightsquigarrow B \sqsubseteq C , B \sqsubset D$
- $B \sqcap \hat{C} \sqsubseteq \rightsquigarrow B \sqcap A \sqsubseteq D, \hat{C} \sqsubset A$
- $\exists r.\hat{C} \sqsubseteq D \rightsquigarrow \exists r.A \sqsubseteq D, \hat{C} \sqsubset A$ 
- $D \sqsubseteq \exists r.\hat{C} \rightsquigarrow D\sqsubseteq \exists r.A, A \sqsubseteq \hat{C}$

A conservative extension of a Tbox $\mathcal{T}$ such as $norm(\mathcal{T})$ adds more informations to 
$\mathcal{T}$ without modifying the information we already have

To decide subsumption its sufficient to consider TBoxes in normal form

 A completion algorithm doesn't derive all consequences of $\mathcal{T}$ , but it derive all of the atomic subsumptions
 $A \sqsubseteq B$ with $A, B \in N_C \cup \{\top, \bot\}$  

## Properties of $\bot$
$\bot$ on the left is a contradiction
$\bot$ on the right is more complex

considering the TBox
$A \sqsubseteq \exists r.B \ \ \ \ \ \ B \sqsubset \exists s.C \ \ \ \ \\ C \sqsubseteq \bot$ 

- C cannot exists as no object belongs to C
- B cannot exists
- A cannot exists
Then $A \sqsubseteq \bot$ meaning A has to be subsumed by $\bot$

To prove completeness we need to show that f a consequence is not derived, then $\mathcal{T}$ doesn't entail it, to verify we build a model $\mathcal{I}$ of $\mathcal{I}$ s.t. $A^{\mathcal{I}} \not \subseteq B^{\mathcal{I}}$ `an object in A is not in B`

A completion algorithm generates consequences in normal form, if our TBox has $n$ symbols, then  the completion algorithm derives at most $n^3$ consequences `(polynomial time)`

## Rule application
To apply a rule we have to find
- at most 2 consequences
- one GCI

## $\mathcal{ELI}$
Extension of $\mathcal{EL}$ that allows for inverse roles
GCI's in $\mathcal{ELI}$ can also be understood as predicate rules
- $\exists r^-.A \sqsubseteq B \rightsquigarrow B(x) \leftarrow r(x,y),A(x)$ 
$\mathcal{ELI}$ may look similar to $\mathcal{EL}$ but reasoning in it requires **Exponential Time**

## $\mathcal{ALC}$
$\mathcal{EL}$ has no way to express negations

we can see $\mathcal{ALC}$ as an extension of $\mathcal{EL}$ with the addition of negation $\neg$ 

Abbreviations
- $\bot := A \sqcap \neg A$
- $\top := \neg \bot$
- $C \sqcup D := \neg(\neg C \sqcap \neg D)$
- $\forall r.C := \neg(\exists r.\neg C)$
### Value Restrictions
$Person \subseteq \forall hasChild.Person$ `every Child of a person has to be a person`
$\forall hasAccess.Stairs \sqsubseteq Inacessible$ `every building with stairs as access is unaccessable, a building with no access at all still belongs to this constant as something with no access is till unacesible`

we can say a concept is in NNF if negations apply only to concept names, we also assume that all concepts are expressed in NNF

for $\mathcal{ALC}$ we are gonna describe algorithms for deciding
- concept satisfiability
- TBox consistency
- KB consistency
using a technique called tableaux `a tableaux is a model-constructing mechanism which works over a set of assertions`

To construct a model we decompose a concept into smaller parts

## Tableaux algorithm
- Assert C(a) `we start by asserting an element`
- Decomposition using the Tableaux rules
	- Concepts are in negation normal form
	- A Tableau rule takes an assertion from $\mathcal{A}$ and adds one or two assertions as follows
		- $\sqcap,  \ if \ C\sqcap D(x) \in \mathcal{A}, \ then \ add \ C(x), D(x) \ to \ \mathcal{A}$ 
		- $\sqcap,  \ if \ C\sqcap D(x) \in \mathcal{A}, \ then \ add \ C(x), D(x) \ to \ \mathcal{A}$ 
disjoint union is used to combine two interpretations ($\mathcal{I,J}$) into a new interpretation $\mathcal{I} \oplus \mathcal{J} =(\Delta^\mathcal{I} \cup \Delta^\mathcal{J}, \cdot^\mathcal{IJ})$  

Applying the tableaux algorithm to check if a concept is satisfiable
$A \sqcap \exists r.(A \sqcap \neg C)\sqcap \forall r.(\neg A \sqcup B)$ 

We apply the conjunction rule
$\{A(a), \exists r.(A\sqcap \neg C)(a), \forall r.(\neg A \sqcup B)(a)\}$ 

$\{A(a), r(a,b), A \sqcap \neg C(b), \forall(\neg A \sqcup B) (a)\}$ we simplify the `exists` using the tableaux rules

$\{A(a), r(a,b), A(b), \neg C(b), \forall(\neg A \sqcup B) (a)\}$ we apply the conjunction rule to the first conjunction

$\{A(a), r(a,b), A(b), \neg C(b), \neg A \sqcup B(b)\}$ we simplify the `forall` using the tableaux rule 

$\{A(a), r(a,b), A(b), \neg C(b), \neg A(b)\}$ we simplify the disjunction using the disjunction  tableaux rule by trying to remove `B(b)`, this leads to a contradiction as the object B must belong to both $A \ and \ \neg A$ 

$\{A(a), r(a,b), A(b), \neg C(b), B(b)\}$ we simplify the disjunction using the disjunction  tableaux rule by trying to remove $\neg A(b)$, this leads to no contradiction

**A Concept C is satisfiable if the tableaux algorithm yields a saturated and open set of assertions**

Starting from a saturated and open set $\mathcal{A}$ how do we construct an interpretation $\mathcal{I_A} = (\Delta^{\mathcal{I_A}},\cdot^\mathcal{I_A})$ 

Referring to the previous example:
$\{A(a), r(a,b), A(b), \neg C(b), B(b)\} \rightarrow$ Open set of assertions $\mathcal{A}$ 

Interpretation:
$\Delta^\mathcal{I} =\{a,b\}$
$A^\mathcal{I} =\{a,b\}$
$B^\mathcal{I} =\{a,b\}$
$C^\mathcal{I} = \emptyset$
$r^\mathcal{I} =\{a,b\}$ `all the pairs which are explicitly stated in the set of assertions`

- if $\neg A(a) \in \mathcal{A}, since \ \mathcal{A} \ is \ open,\  then \ A(a) \not \in \mathcal{A}$ 
If the tableaux gives an open and saturated set $\mathcal{A}$ then C is satisfiable `C is sound`

we still have to check for completeness

We have to make the right choice in the disjunction rule

if $\mathcal{I}$ satisfies $\mathcal{A}$ and a rule application on $\mathcal{A}$ yields $\mathcal{B}$, then $\mathcal{I}$ satisfies $\mathcal{B}$

Case analysis for single rules:
$\sqcap$ if $\mathcal{I}$ satisfies $C \sqcap D(a)$ then $\mathcal{I}$ satisfies $C(a)$ and $D(a)$
$\sqcup$ if $\mathcal{I}$ satisfies $C \sqcup D(a)$ then choose to add $C(a)$ to the assertions. $\mathcal{I}$ satisfies $C(a)$ 
$\exists$ if $\mathcal{I}$ satisfies $\exists r.C(a)$ then $\mathcal{I}$ satisfies $r(a,b)$ and $C(a)$
$\forall$ if $\mathcal{I}$ satisfies $C \sqcap D(a)$ then $\mathcal{I}$ satisfies $C(a)$ and $D(a)$ `ancora da sistemare. sbagiato, guarda gli appunti :|`

The tableaux algorithm doesn't consider GCI's

the GCI $C \sqsubseteq D$ is equivalent to $\top \sqsubseteq \neg C \sqcup D$
Every element of the domain must belong to $\neg C \sqcup D$

consider the TBox $\mathcal{T}$ with two GCIs
$A\sqsubseteq B \sqcap \forall r.A$
$B \sqsubseteq \exists r.\neg A$ 

is this TBox consistent?
if we try constructing models:
if we start from the first GCI we have an element with an r successor to $\neg A$ but all it's r successor must go to A `we cannot construct a model`

if we start from the second GCI we are able to construct a model
this way isn't very efficient as the result we get depends on the order we follow to construct the model

to decide satisfiability and consistency in a better way we can apply the tableaux rules
**we need to add a new rule to the tableaux** $\to$ subsumption rule
- $\sqsubseteq$    if $C \sqsubseteq D \in \mathcal{T}$ and $x$ appears in $\mathcal{A}$, add $\neg C \sqcup D(x)$ to $\mathcal{A}$
we still have to transform everything to NNF

example
consider the TBox $\top \sqsubseteq \exists r.\top$ `everybody has an r successor`

$\top(a) \xrightarrow{\sqsubseteq} \exists r.\top(a)$ 

if we keep applying the algorithm we just get an infinite sequence of nodes, but they're all the same $\to$ after recognizing a pattern, further enumeration is no longer informative

![[cycle]]
The cycle isn't mean to represent a cyclic model, it gives the instruction on how to construct a found pattern
- If the cyclic pattern is contradiction free, then the unfolded model is also without contradiction
This doesn't construct a model, it's just helpful to test for satisfiability

---
# Blocking
The set of assertions is seen as a Tree
![[tree]]
Every node will then have a set of cons such as
$Cons(a) = {\forall s.C, B}$ ,A

## Blocking
- The node a is blocked by the node b in $\mathcal{A}$ iff 
	- b is a non-root predecessor of a and
	- $Cons_\mathcal{A}(a) \subseteq Cons_{\mathcal{A}}(b)$ 
with this new 'blocking' concept we can modify all the rules in the tableaux which create new objects $\to$ in this case we modify only the existential rule
- the $\exists$ rule is only applicable to $\exists r.C(a)$ only if a isn't blocked and none of it's predecessor are blocked

Example

insert pic
![[Lesson 1411.jpeg]]
every cons that appears in d also appears in b, meaning $Cons(d)\subseteq Cons(a)$ 
d is blocked

Can blocking guarantee that no infinite derivations are possible?

if $\mathcal{T}$ has n subconcepts. there are a most $2^n$ different sets $Cons_\mathcal{A}$ 
The tree generated by the tableau has depth which is at most $2^n + 2$ and finite width, which is the number of $\exists r.C$ subconcepts

**in theory, to decide TBox consistency exponential time is needed**
in practice, we'll work on TBoxes constructed by humans, which behave in a simpler way

## Other problems
- Satisfiability: to check if C is satisfiable we start the tableau algorithm starting with $\{C(a)\}$
- Subsumption: $\mathcal{T} \vDash C \sqsubseteq D \ \mbox{iff} \ \ C\sqcap \neg D$$ is unsatisfiable

