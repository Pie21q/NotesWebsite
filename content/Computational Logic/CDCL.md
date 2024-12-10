+++
title = 'CDCL'
date = 2024-12-10
draft = false
math=true
+++

Review online lesson 25 / 10 / 2024 for explanation and examples

## CDCL
each step is structured like
$$(V \ | \ F \ | \ \alpha)$$
where
- $V$ is a partial assignment (for example $p_1, p_2, p_3$ or $p_1, \bar{p_2}$), in the end we expect to get either a failure (UNSAT), or a total assignment, where all the literals are present
- $F$ is a set of clauses containing both original clauses and additional clauses which we call 'learnt'
- $\alpha$ can either be the 'search mode', or a clause known as the conflict clause

The initial status is
$$(\emptyset \ | \ F_0 \ | \ *)$$
where
- $\emptyset$ means nothing is assigned yet
- $F_0$ is the set of input clauses
- $*$ specifies we are in search state

## Search State Rules
- Propagation
	given a situation such as $< V \ | \ F, C \vee l \ | \ *>$ , if our current assignment falsifies C ( $V \vDash \neg C$ ), then we have to assume that $l$ has to be true.
	The new situation becomes $< V, l \ | \ F, C \vee l \ | \ *>$.
- Conflict
	given a situation such as $< V \ | \ F, C \ | \ *>$ , if our current assignment falsifies C ($V \vDash \neg C$), then we switch over to conflict state $< V \ | \ F, C \ | \ C>$ 
- Decision
	given a situation such as $< V \ | \ F \ | \ *>$ where the previous 2 rules do not apply, we are free to pick an unassigned literal $l$ to assign, getting a new formula such as $< V, l^d \ | \ F \ | \ *>$ 
## Conflict State Rules
these rules apply when we get to a step which is in conflict state, such as $< V \ | \ F \ | \ C>$ 
(with $V \vDash \neg C$)
- Failure
	if we get to a point where $< V \ | \ F \ | \ \Box>$ , with $\Box \ meaning \ \emptyset$ , we exit with $UNSAT$ 
- Explain Rule
	if we get to a state such as $< V \ | \ F, D \vee \bar{l} \ | \ C \vee l>$ we compute the resolution between $D \vee \bar{l}$ and $C \vee l \ s.t.$  $\frac{D\vee \bar{l} \ \ \ \ C \vee l}{D \vee C}$ .
	we then get to a new situation, which in this case is $< V \ | \ F, D \vee \bar{l} \ | \ D \vee C>$ , this rule could lead us to produce the empty clause, making the algorithm exit with $UNSAT$ 
- Backjumping Rule / Reparation Rule
	if we get in a situation such as $<V_1 l^d V_2 \ | \ F \ | \ C \vee l'>$ with $V_1 \vDash \neg C$ , we can go back to search state by adding $l'$ as a decided literal and $C \vee l'$ as a learnt clause:
	$<V_1, l' \ | \ F, C\vee l' \ | \ *>$ .
	Notice how $V_2$ gets eliminated in the process.