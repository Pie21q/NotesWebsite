+++
title = 'Computational Logic, From SAT to SMT'
date = 2024-10-11
draft = false
math=true
+++


## Propositional Logic 
Refer to the KR notes on the same topic

Remember that
$$ \rightarrow means \space if, \space while\space \leftrightarrow \space means \space if \space and\space only\space if $$
Some expressions make perfect sense, like
$$(p\vee q) \rightarrow r$$
`If it rains (p) or it snows (q), then i will take an umbrella (r)`

while others are meaningless
$$pq)) \rightarrow r$$
## Formula
A formula is a string of characters which follows the following rules
$$ \begin{flalign}Every \space p \in L \space is \ a \ formula \ (rule \ n1)&& \end{flalign}$$$$ \begin{flalign} if \ all \ A,B's \ are \ formulas, then \ (A \vee B) \ and \ (A \wedge B) \ are \ also \ formulas \ (rule \ n2) && \end{flalign}$$
we can also create a tree from the main formula, where the nodes are built using rule 2 and the last elements using rule 1

Some conventions are used to eliminate some brackets

$$ \begin{flalign} a*b=c, \ product \ is \ stronger \ than \ sum && \end{flalign}$$
in the same way, in computational logic
$$ \begin{flalign} \neg \ is \ stronger \ than \wedge \vee, and \ they're \ stronger \ than \ \rightarrow && \end{flalign}$$
>for example
>$$ ((\neg p) \rightarrow (q \vee r)) = \neg p \rightarrow q \vee r $$

### How to compute implication 
Implication's more problematic, as in natural languages `such as english`, implications can have different meanings. 
In Logic this couldn't work, so implication takes a meaning similar to the one present in Computer science

==The only way i can falsify an implication is making the antecedent true and the other true

$$ \begin{flalign} A \rightarrow B \ can  \ be \ false \ exclusively \ when  \ A  \ is \ false && \end{flalign}$$

we can define implication as 
$$ V(\neg A \vee B) = V(\neg(A \vee \neg B)) $$

also 
$$ A \leftrightarrow B \equiv (A \rightarrow B) \wedge (B \rightarrow A)$$

$$ \neg \neg \neg \neg \neg p = \neg p$$

# Sat
Sat is a program that can be used to find satisfiable solutions for a given logic problem 

With heuristics we refer to a method which is not fully refined nor optimized, but it is still considered good enough to reach the resolution of a problem

Resolution
DPLL `Davis-Putnam-Logemann- Loveland` is an algorithm used in the resolution of SAT problems, it works by assigning values to boolean variables and backtracking whenever it runs into a contradiction.

## Tautology
A value $\mathcal{A}$ is a Tautology iff $V(\mathcal{A}) = 1 \ \forall V$
A value $\mathcal{A}$ is unsatisfiable iff $V(\mathcal{A}) = 0$ `also called a contradiction`
2 Values $\mathcal{A}$ and $\mathcal{B}$ are equivalent iff $V(\mathcal{A}) = V(\mathcal{B})$
2 Values $\mathcal{A}$ and $\mathcal{B}$ are equi-satisfiable if they're both satisfiable or unsatisfiable

## Some definitions
- Atom: Propositional Variables  $p, q, r$
- Literal: Atoms or negated atoms $p, q, \neg p$ 
- Clause: Disjunction of literals $p, \neg p, p \vee q, p \vee \neg q$
- Cube: Conjunction of literals$p, \neg p, p \wedge q, p \wedge \neg q$
- Conjunctive normal form `CNF`: Conjunction of clauses $p \wedge (q\vee \neg r)$
- Disjunctive normal form `DNF`: Disjunction of clauses $p \vee (q\vee \neg r)$
- Negation normal form `NNF`: No $\rightarrow$ and $\neg$ only in front of atoms $\neg p \wedge (q \vee \neg r), \neg p$, `negations have to be only in front of atoms` 

What will we do in the lab?
>Take a set of formulae and find, `if possible`, an assignment which makes all of them true, producing a set of equi-satisfiable clauses (As an intermediate step we'll get a set of formulae in NNF)

keep in mind that
> Every formula is equivalent to a formula in NNF, also the conversion happens very quickly
> $A \rightarrow B \rightsquigarrow \neg A \vee B$
> $\neg(A\wedge B) \rightsquigarrow \neg A \vee \neg B$  
> If you replace a formula C with a formula D with some D' equivalent to D, then the result is equivalent to C


CNF Transformations can be done in 2 ways
- Non structural way makes the formula exponentially long but produces logical equivalences `For our purposes, in manual exercises is better to use non structural way`  
	- Using non structural way we transform our formulae in a CNF $A \vee (B\wedge C) \rightsquigarrow (A\vee B) \wedge (A\vee C)$  `A appears 2 times instead of one`


- Structural Way is more efficient but only produces satisfiability `A tool like Z3 will use a structural way to compute problems`

To convert into CNF we use 3 formulas 
- $A \rightarrow B \rightsquigarrow \neg A \vee B$ 
- $\neg (A\rightarrow B) \rightsquigarrow A \wedge \neg B$
- $(A \wedge B) \vee C \rightsquigarrow (A \vee C) \wedge (B \vee C)$ "From NNF to CNF"

For all rules for simplification also reference KR's notes for Boolean Algebra (DeMorgan's Law and distributivity rules)
---
How to recognize correct reasoning
>`For example: If it rains (p) i take an umbrella (q), it does not rain, so i do not take an umbrella is wrongful reaasoning, as i could still be taking the umbrella, the proposition above only forces me to take an umbrella if it's raining

$p \rightarrow q$
$\neg q$  so $\neg p$ 

This has to be true for every V, so we have to check if for every V $V(p\rightarrow q) = 1 \  and \  V(\neg P) = 1$
Computing the truth table we can se that $\neg q$  so $\neg p$  isn't true