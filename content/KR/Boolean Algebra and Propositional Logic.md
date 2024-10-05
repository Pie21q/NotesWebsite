+++
title = 'Boolean Algebra and Propositional Logic'
date = 2024-10-05T12:08:51+02:00
draft = false
math = true 
+++



Boolean algebra refers to the manipulation of truth values through logical operations.
We are gonna consider just 2 truth values
- True `1`
- False `0`
and 3 Boolean Operators to manipulate the values
- Conjunction (∧) `And`
- Disjunction (∨) `Or`
- Negation (¬) `Not`

In Boolean Algebra we compute complex expressions of Logic Operators containing variables

# Propositional Logic
Propositional logic is used to combine propositions and studying their truth values

- Atomic Propositions state one fact or one property `Mammals are vertebreae`
## Formulas
==Formulas== are used to combine propositions
[[Logic]] is still a language so we must specify
- Which kind of expressions are allowed (Syntax)
	- Every propositional variable is a formula
	- Given that `x` and `y` are formulas, then `¬x` or `x∧y` are also formulas `eg. the negation of a formula it's still a formula`
- What do they mean (Semantics)
	- The full formula can be either `true` or `false`, depending on the truth of its components
	- A 'Valuation' is the assignment of a truth value to each variable
		`eg. one valuation of V with 3 parameters could be
		`V(x) = 0
		`V(y) = 0
		`V(w) = 1`
	- The valuation then needs to be extended to Formulas `V(¬x) = ¬V(x) => 1 iff V(x) = 0
	- Three types of formulas
		- Tautologies `always 1 - all tautologies are equivalent ≡`
		- Contrapositions  `always 0 - all contradictions are equivaent ≡`
		- Non-Tautologies `All of the other kinds`
	- A Formula with `n` variables is known as a Function, mapping `n` truth values to just `one`
- Formulas are characterized by their behavior as a function 
- Two formulas are equivalent `≡` iff they have the same truth table `even if they look very different`
T = Tautologies `Top`
⊥ = Bottom `Bottom`

$X \wedge \top = X,\ \ \ \ X \vee \top = \top$
$X \vee \bot = X\ \ \ \ X \wedge \bot = \bot$

It's possible to imagine other operators 
- NAND `Not both true`
- implication `if x then y`

All operators can be expressed trough the 3 basic operators
Formula for implication:$$ X \rightarrow Y \equiv \neg x \vee y $$
Fundamental Equivalences
DeMorgans Equivalence
$$ \neg(x\wedge y) \equiv \neg x \vee \neg y $$
$$ \neg(x\vee y) \equiv \neg x \wedge \neg y $$
Useful to push the negation from outside a complex formula to inside it's parts

Distributivity
$$ x \wedge (y \vee z) \equiv (x \wedge y) \vee (x \wedge z) $$
$$ x \vee (y \wedge z) \equiv (x \vee y) \wedge (x \vee z) $$
Involution
$$ \neg \neg \equiv x $$

# What does all this have to do with KR?
Knowledge bases are sets of formulas used to constraint the relevant interpretations
###### [[Representing Knowledge as Rules]]