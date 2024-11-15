+++
title = 'First Order Logic"
date = 2024-11-08
draft = false
math=true
+++

All man are mortal
Socrates is a man
---
Socrates is mortal

- $\forall x (Man(x) \rightarrow Mortal(x))$
- $Man(Socrates)$
- $Mortal(Socrates)$

First Order logic includes
- Names for objects `individual constants`
- Names for operations `function symbols`
- Names for properties and relations `operations`

$\mathcal{l} = < \mathcal{F, P}, \alpha >$ 
where
$\mathcal{F}$ is the set of operation symbols
$\mathcal{P}$ is the set of predicates
$\alpha$ is a function which tells us how many arguments an operation can take
- $\alpha(+) = 2$ `the sum takes 2 arguments (numbers)`
- $\alpha(\pi) = 0$  `Pi doesn't take anything as an argument`

whenever we start solving a problem in First Oder Logic we must declare a language

---

- Terms `used to indicate objects`
	- Terms without variables are known as `Ground Terms`
- Formulae `used for assertions`
	- formulae are obtaining applying predicates to terms and then connectives ($\wedge, \vee, \neg, \rightarrow$) and quantifications ($\forall, \exists$)

for example
- $x + y - 3 \ or \ 3\cdot 5$ are terms, as they both represent a number `terms are built ul using variables, constants and operators`

Formal definition of a formula
- if $P \in \mathcal{P}, \alpha(P) = n, \ and \ t_1,...,t_n \ are \ terms, \ then \ P(t_1,...,t_n) \ is \ a \ formula$ `definition for atomic formulae`
- if A, B are formulae, so are $(A\wedge B), (A \vee B), (A \rightarrow B), (\neg A)$
- if x is a variable and A is a formula, $(\exists x A) (\forall x A)$ are formulae
### Example
```
suppose your langueage has a binary function symbol F, a unary predicate P and constant a,b.
Write down a ground term, a non ground term, a ground atomic formula, a non ground literal in this language
```
- Ground terms = $a, b, f(a,a), f(b,b)$
- Non ground terms = $f(x,a) , f(x,y)$
- Ground atomic formulae = 
An occurrence of a variable is bound iff it's located inside of a subformula of the kind $\forall x B \exists x B-$ 

A formula is open iff it does not have quantifiers
A formula is universal iff it's of the kind $\forall x_1,...,\forall x_n A$ where A is open
a formula is existential iff it's of the kind $\exists x_1,...,\exists x_n A$ where A is open

## Substitution $A(t_1/x_1,...,t_n/x_n)$
Y mean the formula obtained from A by replacing the free variable only


for example
$\forall x R(x,a) \rightarrow Q(x)$, we replace x with f(y)
$\forall x R(x,a) \rightarrow Q(f(y)$ first x isn't replaced as it's ground

instance: remove the universal quantifier and replace the quantified variable with a term
Instantiation can be dangerous if it's used with non ground terms

$\forall x \exists y(x,y) \rightsquigarrow \exists y(y,y)$  this is wrong, because of the presence of non ground terms

to deal with these cases we have to remove the bounded variable, in a way that the term which has to be replaced doesn't contain it.

`this will not happen in the exeercises as we will only work with ground cases` $\rightarrow$ `keep it in mind but dont stress about it :)`