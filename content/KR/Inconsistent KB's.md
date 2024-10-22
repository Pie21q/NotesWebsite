+++
title = 'Inconsistent KBs'
date = 2024-10-22
draft = false
math = true
+++

In case of inconsistency, the canonical model might not be a model of our KB
To determine if a KB is inconsistent we have to keep in mind some things
- Constraints may lead to contradictory knowledge
	- Platypus(perry) $\leftarrow$
	- Duck(perry) $\leftarrow$
	-  $\leftarrow$ Duck(x), Platypus(x)
	Inconsistent as an object can't be both a platypus and a duck due to the **Principle of Explosion**

A KB is inconsistent iff it's canonical interpretation is unsound
Reasoning requires us to look at the canonical interpretation only

The grounding of a predicate KB is just a propositional KB with elaborate propositional variables 