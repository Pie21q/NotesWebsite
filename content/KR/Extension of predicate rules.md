+++
title = 'Extension of predicate rules'
date = 2024-10-22
draft = false
math = true
+++

# Rules as programming 
we can read the rule $H \leftarrow B$ as "If B is true, then H is true"
Knowledge is then propagated in one direction, other than that, there are no limits beyond constraints.
What if we wanna express that a person has at most / at least 2 parents, or that someone is alive iff they are not dead (they are either alive or dead, they have to be one, they can't be both)?

with constraints we can represent negations
- $\leftarrow$ Platypus(Phineas) (Phineas is not a platypus)
- $\leftarrow$ Alive(x), Dead(x) (you cant be both alive and dead)
what if we wanna represent the fact that you cannot be both alive and dead or specify a property of mammals which aren't platypi.

Also keep in mind that due to **Domain Closure** rules can never introduce new objects

Due to the fact that predicate KB's are limited to Horn Clauses, we cannot express case enumeration
- If it is a weekday, then it is Monday, or Tuesday, or...
- Monotremata are platypi or echidna
we cant actually know if it's Monday or Wednesday or if it is a Platypi or an Echidna

We want to extend our predicate rules in order to deal with negations, anonymous individuals and disjunctions

We can do this by weakening some of the requirements on rules
- To get a disjunction we must remove the requirement for horn clauses
	- We can allow for arbitrary clauses in our rules
- to allow anonymous individuals we remove the requirement for which every variable in the head must appear in the body
	- HasChild(x, y) $\leftarrow$ Parent(x)
		iff somebody is a parent, then there is one object which is the child
- to allow for negations we still have to remove horn clauses
	- Dead (x) $\vee$ Alive (x )

