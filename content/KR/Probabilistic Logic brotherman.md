+++
title = 'Probabilistic Logic'
date = 2025-02-20
draft = false
math = true
+++


The previous KR languages we studied all assume knowledge to be perfect
no more

probabilistic logic satisfies some properties
- $P(\bot) = 0$
- $P(\neg \varphi) = 1 - \varphi$
- $P(\varphi \vee \psi) = P(\varphi) + P(\psi) - P(\varphi \wedge \psi)$

Probabilistic Logics are not **Truth functional**
	Knowing $P(\varphi)$ and $P(\psi)$ is not enough to find out $P(\varphi \wedge \psi)$ or $P(\varphi \vee \psi)$ 

There exists 2 types of uncertainty
- Type I (Statistical)
	75% of BAI students are Italian
	(probability of a BAI student to be Italian is 75%)
- Type II (subjective)
	the probability of Rafael having a daughter is 40%

Clauses, facts, and rules
- A probabilistic horn clause is an expression $p::\gamma$ where
	- $p \in [0,1]$
	- $\gamma$ is an horn clause
	- A probabilistic fact is an expression of the kind $p::x \leftarrow$
	- A probabilistic rule is an expression of the kind $p::x \leftarrow y_1,...,y_n$

A probabilistic Knowledge Base is a finite set $K$ of
- classical rules and facts $K_C$
- probabilistic rules and facts $K_P$

we can use $p::\gamma$ to express that $p$ is the probability of $\gamma$ , meaning we have 2 scenarios
- One where $\gamma$ holds
- One where $\gamma$ doesn't hold

We consider them both **Multiple Worlds Semantics**

What if we have more than one probabilistic clause
- We also need more worlds

2 ways of dealing with multiple probabilities
- Assume independency (Multiply the joint probabilities for each world)
- Consider entropy and use the distribution that maximizes entropy

The probability of a consequence $\alpha$ is the sum of the probabilities of all the worlds that entail $\alpha$

