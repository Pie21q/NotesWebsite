+++
title = 'Exams Theory Questions'
date = 2025-01-27
draft = false
math=true
+++


- Distinguere e caratteristiche CNF 
	-Conjunctive Normal Form, Set of clauses made up of disjunction
    
- come trasformo NNF a CNF e viceversa '
	-Transformation between NNF and CNF is done through distribution rules
		$$(C \wedge D)\vee F := (C \vee F) \wedge (D \vee F)$$
    
- <mark style="background-color: lightblue">cosa dice l’herbrand theorem, cosa implica, come si usa  </mark>
		A set of universal sentences T is unsatisfiable (in predicate logic) iff there is a finite set of instances of formulae in T whose propositional abstraction is unsatisfiable (in propositional logic)
		To Check for satisfiability we have to consider all constants which are present in the Herbrand's universe (These are infinite, so we have to consider just the ones which are relevant to the resolution of the problem)
    
- una variable come fa ad essere bounded / free? 
		We call a variable which is preceded by constructors such as $\forall \ or \ \exists$ **Bounded**, a variable which isn't bounded is free
		- $x$ is free
		- $\exists x$ is bounded
		In the formula $\forall x R(x, f(x), y) \vee R (x, f(x), y)$
			- In the first half $x$ is bounded by $\forall xR$ , this applies to both $x$'s, while $y$ isn't bounded and is therefore free
			- In the second half $x$ is no longer bounded, and the same is true for $y$, meaning both are free
    
    
- Cosè un term e un literal? 
	    - Terms are used to describe objects, they are made up of just the basic elements of a language and don't contain logic operators
	    -Terms can be variables, constants and functions
- cos’è una ground instance 
		in an universal sentence, ground instances are the sentences of the kind $A(t_1/x_1, t_n / x_n)$, where $t$ are ground terms
- cos’e un ground term 
	    A ground term is a term made up of constant's
- cosa significa skolemizzare 
	    Skolemization is used to remove existential quantifiers from a set of clauses in PNX by substituting them with a skolem function $f$ of arity equal to the number of universal quantifiers to the left of the existential one
    
- cos’è una T-conflict rule, perchè, quando la uso e come la uso? 
		The T-conflict rule is a rule that can be applied during CDCL(T) which allows us to switch from the state <V | F | \*>  to a state <V | F, C | C> if $C := l_1 \vee l_n$ and $\bar{l_1} , \bar{l_n} \subseteq V$ is not T-satisfiable (The literals which have been either propagated or decided aren't compatible with the original set of clauses)    
- satisfiability criterion for a conjunction of atoms in integer difference logic.  
    
- statement of the refutational Completeness Theorem for propositional resolution calculus.  
	- In a adequately designed calculus $\mathcal{R}$, a saturated set is inconsistent iff it contains an empty clause. An example of this can be seen through resolution calculus

    
- Fourier-Motzkin procedure  
	- $x \not < 0 \rightarrow x \geq 0$
	- $x \not = 0 \rightarrow x > 0 \wedge x < 0$ 
    
- cosa comporta l’herbrand universe, come cambia tra finite e infinite? 
	- The herband universe is finite if only constants appear in it, while it's infinite if it contains at least one unary function symbol $f$
    
- <mark style="background-color: lightblue">the condition for a theory to be stably infinite.  </mark>
	- A Theory $T$ is stably infinite if every T-satisfiable constraint is satisfiable in an infinite model of $T$ 
    
- reflexivity, symmetry, transitivity axioms for equality; write down also the conguence axioms regarding the symbols of L.  
    
- Write down the definition of a Horn clause.
	- An Horn clause is a disjunction of literals with at most one positive
    
- Formulate the propositional resolution rule.  
	- To apply the resolution rule we take 2 clauses which contain the same literal in different polarities, to get the conclusion we simply remove the shared literals and merge the two resulting clauses 
    
- <mark style="background-color: lightblue">Explain Nelson-Oppen combination procedure.  </mark>
	- The Nelson-Oppen procedure is applied when working with a combination of different theories: Supposing we have as input a finite set of literals $S$ in a language $L_1 \cup L_2$ of $T_1 \cup T_2$, we are able to apply a flattening procedure to decompose $S$ in $S_1 \cup S_2$ where all the literals of $S_n$ belong to $T_n$
	- Proposition: Let $T_1 = (\mathcal{L_1, C_1)}$ and  $T_2 = (\mathcal{L_2, C_2)}$ be two **stably infinite** theories and let $S_1, S_2$ be two sets of flat literals in $\mathcal{L_1,L_2}$ respectively containing the set of constants $C$. if for each $c_1,c_2 \in C$  we have that either $c_1 = c_2  \ or \ c_1 \not = c_2$ belong to $S_1 \cap S_2$, then the $T_1$-satisfiability of $S_1$ and the $T_2$-satisfiability of $S_2$ imply the $T_1 \cup T_2$-satisfiability of $S_1 \cup S_2$ 
    
- Formulate the subsumption rule as a simplification rule in the propositional resolution calculus.  
	- In propositional resolution the most common rule used for simplification is subsumption: if in the current clause we have both $C$ and $C'$ with $C \subseteq C'$ , then $C'$ Can be eliminated

    
- <mark style="background-color: lightblue">Give an example of a convex theory </mark>
	- A theory is convex if the following property holds for any finite set of literals $S$ and for any finite, non empty set of equalities between variable 
		- if $x_1 = y_1 \vee x_n = y_n$ is a $T$-logical consequence of $S$, then there exists a $j$ such that $x_j = y_j$ 
		- some convex theories are EUF and real linear arithmetic 
    
- Formulate the T-conflict rule in the CDCL(T) procedure.  
	- The T-conflict rule is a rule that can be applied during CDCL(T) which allows us to switch from the state <V | F | \*>  to a state <V | F, C | C> if $C := l_1 \vee l_n$ and $\bar{l_1} , \bar{l_n} \subseteq V$ is not T-satisfiable (The literals which have been either propagated or decided aren't compatible with the original set of clauses)    
    
- Give an example of a non-convex theory.  
	    IDL and Array Theory
- Explain the T-propagation rule of the CDCL(T) procedure.  
	    if we are in the state of <V | F |\*> we can pass to the state of $< V, l | F, D \vee l | *>$ if $\neg D \wedge \bar{l}$ is not $T$-satisfiable $V \vDash \neg D$ and $l$ are not defined in $V$   
- Explain an algorithm to check satisfiability of a finite set of literals in  
    integer difference logic (you may use examples to show it, if you like).  
    
- what is an unsat core?  
	    The unsat core is the minimal possible set of unsatisfiable assertion
- when a formulae is in prenex form? 

    
- Write down a ground L-atom whose root symbol is the identity pre- dicate and a ground L-atom whose root symbol is not the identity predicate.  
    
- cos’è un indentity predicate 
    
- what structural transformation does? 
    
- caratteristiche congruence closure 

- <mark style="background-color: lightblue">Church's Theorem </mark>
	There exists no algorithm that decides $T \vDash B$, not even for empty T
	
	We can always tell whenever something is UNSAT in First Order Logic, but sometimes we may not be able to tell if it's SAT
	we have to look for a 'semi-algorithm' (it may not terminate) to check unsatisfiability of a (finite) set of sentences T

- Array Theory (3 steps to reduce the system to EUF)
	- 1) Eliminate $a \not = b$ by introducing a new constant i
	$$a \not = b \rightarrow rd(a,i) \not = rd(b, i)$$
	- 2) For each literal $a = b$ we add the atom 
	$$rd(a, i) = rd(b, i)$$
		and for every literal $a = wr(b,i,e)$ we add the atom $rd(a,i) = l$ and a clause $i = j \vee rd(a,i) = rd(b , j)$ 

	- 3) For every constant $a$ we introduce a unary function $f_a$ and replace $rd(a, i)$ with $f_a(i)$ 

## Equality properties
- reflexivity: $\forall x \ \ x = x$
- Symmetry: $\forall x \forall y (x = y \wedge y = x)$
- Transitivity: $\forall x \forall y \forall z (x=y \wedge y = z \rightarrow x = z)$
- Congruence 
	- with functions $\forall x_1 \forall x_n \forall y_1 \forall y_n (x_1 = y_1 \wedge x_n = y_n \rightarrow f(x_1, x_n) = f(y_1, y_n)$
	- with predicates $\forall x_1 \forall x_n \forall y_1 \forall y_n (x_1 = y_1 \wedge x_n = y_n \rightarrow P(x_1, x_n) = P(y_1, y_n)$

