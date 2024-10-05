
+++
title = 'Computational Logic, from SAT to SMT'
date = 2024-10-05T12:08:51+02:00
draft = false
math = true 
+++



## Propositional Logic 
Refer to the KR notes on the same topic

Remember that
$$\rightarrow means \space if, \space while\space \leftrightarrow \space means \space if \space and\space only\space if$$
Some expressions make perfect sense, like
$$(p\vee q) \rightarrow r$$
`If it rains (p) or it snows (q), then i will take an umbrella (r)`

while others are meaningless
$$pq)) \rightarrow r$$
## Formula
A formula is a string of characters which follows the following rules
$$ Every \space p \in L \space is \ a \ formula \ (rule \ n1)  $$$$  if \ all \ A,B's \ are \ formulas, then \ (A \vee B) \ and \ (A \wedge B) \ are \ also \ formulas \ (rule \ n2)   $$
we can also create a tree from the main formula, where the nodes are built using rule 2 and the last elements using rule 1

Some conventions are used to eliminate some brackets

$$  a*b=c, \ product \ is \ stronger \ than \ sum   $$
in the same way, in computational logic
$$  \neg \ is \ stronger \ than \wedge \vee, and \ they're \ stronger \ than \ \rightarrow   $$
>for example
>$$ ((\neg p) \rightarrow (q \vee r)) = \neg p \rightarrow q \vee r $$

### How to compute implication 
Implication's more problematic, as in natural languages `such as english`, implications can have different meanings. 
In Logic this couldn't work, so implication takes a meaning similar to the one present in Computer science

==The only way i can falsify an implication is making the antecedent true and the other true

$$  A \rightarrow B \ can  \ be \ false \ exclusively \ when  \ A  \ is \ false   $$

we can define implication as 
$$ V(\neg A \vee B) = V(\neg(A \vee \neg B)) $$

also 
$$ A \leftrightarrow B \equiv (A \rightarrow B) \wedge (B \rightarrow A)$$

$$ \neg \neg \neg \neg \neg p = \neg p$$

