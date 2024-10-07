+++
title = 'Representing Knowledge as Rules'
date = 2024-10-05T12:08:51+02:00
draft = false
math = true 
+++

also see [[Boolean Algebra and Propositional Logic]]
# Clauses
a clause is a ==disjunction== of literals `(variables or negated variables)`

some clauses
$$ x \vee y \vee \neg z $$
$$ \neg x \vee \neg y $$
## Horn Clause
A Horn clause has at most 1 positive literal

$x$
$x \vee \neg y \vee \neg z$

We will represent Horn clauses in a different way
$(x_1 \wedge x_2 \wedge ... \wedge X_n) \rightarrow y$
Meaning if all X's are true, then y must be true as well


## Facts 
Another type of horn clauses consisting of just one, positive literal
$$ X = X \vee \bot = x \vee \neg \top $$
which becomes
$$ T \rightarrow x $$
Meaning if true is true, x must be true, so `x must be true`

## Non definite Horn clauses
Horn clauses lacking the positive literal
$$ \neg x_1 \vee \neg x_2 $$
# Knowledge Representation
Based on what has been said above, a `Knowledge Base` is a finite set of rules
for example
$$ Platypus \leftarrow Monotreme, Venomous, DuckBilled $$
An individual which is a Monotreme, Venomous and DuckBilled is necessarily a Platypus

$$ Monotreme \leftarrow Mammal, Oviparous $$
An individual which is both Mammal and Oviparous must be a Monotreme

`Being Knowledge, we consider all rules to be true`

Considering that a Knowledge Base is a set of formulas such as
$$ x_1, ..., x_m $$
and we believe them to be true, then we believe that
$$ x_1 \wedge ... \wedge x_m \space is \space true $$
we can then say Y is a consequence of this and Y is a Tautology

`All of this is abit complex so we will use a simpler notation

$K \models \phi$, Meaning that K entails $\phi$ 

## Unit Resolution
In case of rules, this is called `Truth propagation`

$y \leftarrow X_1, . . ., X_2$  means if all conditions are true, then y is also true

To guarantee that y is true, $X_i (1 \le i \le n)$ need to be true 

$y \leftarrow X_1, . . .,X_{i-1}, X_i, X_{i+1} X_n$ , We already know that $X_i$ is true so we can ignore it in the body of the first rule `We only care about the truth value of the remaining variable`

## Fact Extraction Algorithm

Input: a KB K `A KB is just a set of horn clauses`
Output: All the true facts given K

```
While 
	there is a fact x and a rule with x in the body do remove x from the body of all rules
return
	all facts in K
```

The KB without facts in the body is called __Redux__

for example
$y \leftarrow x, z ,w$
$z \leftarrow$
$w \leftarrow$

Our algorithm can remove both z and w from all equations since they're facts
The `Redux` of this KB becomes
$y \leftarrow x$
$z \leftarrow$
$w \leftarrow$

Keep in mind that Unit resolution is `sound`, meaning it only returns consequences  `(No false positives)`, meaning 

if $\nu$ is a valuation such that $\nu(y \leftarrow X_1, ..., X_n)=1 = \nu(x_i \leftarrow)$ then $\nu(y \leftarrow X_1,X_{i-1}, ...,X_{i+1}, X_n) = 1$

From the top set of equation we know that $X_i$ has to be `true`,
Also, this means that $K \rightarrow \hat{K}$ Is a Tautology
	Also, $K \rightarrow x$ is a tautology if x is a fact in $\hat{K}$ 

Is a KB complete? (`Does it return all consequences of K?`)
> No, it only returns **Facts** entailed by K

A rule such as  $\leftarrow$ Is a contradiction ($\bot$), Meaning the knowledge base itself is contradictory as it is `Impossible to satisfy

We can rewrite  $\leftarrow \ as \ \top \rightarrow \bot$ , Which we evaluate to `0`

In this case, We can apparently satisfy the KB but not the redux, in this case, the original KB is itself unable to be satisfied `(an insatiable KB is known as inconsistent)`

## Consequences of Inconsistency

considering $K \models \phi$ , if there's no evaluation to satisfy K, K is defined as inconsistent, Meaning every formula $\psi$ is a consequence of K and will always be `true`

If K is consistent, then the process resolution is complete with respect to facts, if $x$ is not a fact i. $\hat{K}$, then it is not a consequence of K

We are now able to extracts all (`but only`) the facts entailed by $K$

## Complex entailments 

In the case of $K \models y \leftarrow X_1, . . . , X_2$, a fact extraction algorithm won't be able to return a fact.
This case is known as a `Complex entailment`, meaning "If  all $X_n$ 's are true, then y is also true" 
In this case, the only relevant valuations are the ones which satisfy K and make all $X_n$ `true`

To solve this we have to verify $K \wedge \bigwedge^n_{i=1} X_i \models y$ , Meaning we add all $X_i$ as implications to the knowledge base temporarily, such that $\ \leftarrow X_i$ , and then we study the consequences of the new implications

## Computational Complexity
With the term `Computational Complexity` we refer to the number of operations needed to find the consequences `How long will it take us to find the answer`

The number of steps needed is equal to $n * m \ steps$ , where K has n rules and m variables

## Properties of Rules
Rules are used to define a simple KR language, which is useful to express basic properties

For example, the expression "Fathers are male parents", becomes
$father \leftarrow male, parent$, while the expression "monotremata are egg-laying mammals becomes $monotreme \leftarrow mammal, oviparous$" 
This language is limited by it's `inexpressivity`, as you cant express relationships between object `(If we are talking about parents, we arent able to discern between grandparents, uncles or siblings)`, as to do this we need to use **Predicate Logic**

