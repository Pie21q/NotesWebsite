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
Meaning if true is true, x must be true, so ==x must be true==

## Non definite Horn clauses
Horn clauses lacking the positive literal
$$ \neg x_1 \vee \neg x_2 $$
# Knowledge Representation
Based on what has been said above, a ==Knowledge Base== is a finite set of rules
for example
$$ Platypus \leftarrow Monotreme, Venomous, DuckBilled $$
An individual which is a Monotreme, Venomous and DuckBilled is necessarily a Platypus

$$ Monotreme \leftarrow Mammal, Oviparous $$
An individual which is both Mammal and Oviparous must be a Monotreme

==Being Knowledge, we consider all rules to be true==

Considering that a Knowledge Base is a set of formulas such as
$$ x_1, ..., x_m $$
and we believe them to be true, then we believe that
$$ x_1 \wedge ... \wedge x_m \space is \space true $$
we can then say Y is a consequence of this and Y is a Tautology

`All of this is abit complex so we will use a simpler notation

$$ K \models Y $$