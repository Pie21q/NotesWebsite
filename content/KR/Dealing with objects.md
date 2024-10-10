+++
title = 'Dealing with objects'
date = 2024-10-10
draft = false
math=true
+++

`Propositional logic` is able to deal with only one item at a time
What if we want to relate different objects?
- Ana is a professor
- Ana supervises bob
or
- A grandparents is the parent of a parent
- Uncles have siblings who are parents

What we have to do is extending the rules in order to handle predicate knowledge
uncle(x) $\leftarrow$ sibling(x, y), parent(x, y)

From proposition to predicates

- **Mammal** is a `propositional variable` which is either True `or` False

we can then represent more informations through predicates such as 
- Mammal(Dumbo)
- Parent(Ana, Bob) $\rightarrow$ Ana is the parent of bob `this is a proposition and can be both True or False`
What about representing implicit constants?
>we use placeholders, also called variables

- Parent(Ana, $x$) $\rightarrow$ Ana is the parent of X, the truth value depends on the value of X
We need to give a `scope` to our variable X
- $\exists x$.parent(Ana, $x$) $\rightarrow$ it exists at least one constant that makes it true
- $\forall x$.parent(Ana, $x$) $\rightarrow$ It's true for every constant
 For KR we wont use the full `predicate logic`, just the concepts as stated above

## Predicate logic Syntax
- Constants $\mathcal{C}$ : a, b, c,...
- Unary and Binary predicate symbols $\mathcal{P}$: P, Q, R `(Unary and Binary based on the amount N of costants defined in predicates such that Mammal(N) )`
- Variables $\mathcal{V}$ : x, y ,z
- With 'Terms' we refer to both **Constants** and **Variables**

Some examples of predicates can be
- P(t)
- Q(t, s)
A `Literal` can be both a predicate or the negation of it
A Predicate Horn clause is a disjunction of literals with **At most one positive**

P, R are used as `Unary predicates` while Q is used for `binary` ones

Writing a clause in rule form can be done in the same way as `Propositional Logic`
$$Q(x,y) \leftarrow Q(b,y), \  P(x), \ R(z)$$
For example
grandparent(x, y) $\leftarrow$ parent (x, z),  parent(z, y)
If an object X is the parent of another parent which has a child Y, then X is the parent of Y $\rightarrow$ `X is the grandparent of Y`

Predicates can be used to represent
- Properties of objects (Unary predicates)
- Relationships between objects (Binary predicates)
Propositional valuations are no longer enough as we have to specify which objects satisfy properties and relations

## Interpretation Based Semantics
Interpretations $\mathcal{I} = (\Delta^{\mathcal{I}}, \cdot^{\mathcal{I}})$  are based on two components
- A domain $\Delta^I$ 
- An interpretation function $\cdot^I$   
- $a^{\mathcal{i}} \in \Delta^{\mathcal{I}}$ 
- if P is unary then $P^{\mathcal{I}} \subseteq \Delta^{\mathcal{I}}$ 
- if P is binary then $P^{\mathcal{I}} \subseteq \Delta^{\mathcal{I}} \times \Delta^{\mathcal{I}}$

Based on this, we interpret constraints as Objects, unary predicates as classes of objects with the property, Binary predicates as relations between objects

## Graphs
A graph is a collection of points (nodes) and arrow (edges) which connect them, we can also express interpretations in the same way, using `labeled graphs`

when the interpretation $\mathcal{I}$ makes the body true, it also makes the head true
## Canonical interpretation Construction
 To build a canonical interpretation you need
 - An empty interpretation
 - All the necessary ingredients
 
To actually construct a canonical interpretation you need three steps
- Create all relevant nodes
- Add Facts
- Propagate Rules
Traditionally, canonical interpretations follow a monotonically constructive approach, meaning all steps can only add elements, but never delete

This is mostly good for definite Horn Clauses, while it's pretty bad for non definite ones (Constraints) $\rightarrow$ During the construction of a canonical interpretation we ignore all constraints

the **Domain** is the set of all constraints 

For every rule i go through every possible substitution and force on the head every one which makes the body true 