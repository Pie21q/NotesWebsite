- `(declare-const p Bool)` is declaring a variable named P
- `;` comments are done through semicolons
- formulas are declared using `not, and, or, =>, =`, the symbols must be prefixed, for example to write $p \vee q$  you would write `(or p q)`
- `(assert(formula))` adds the formula to the check-sat
- `(check-sat)` verifies if the formula can be True

To check if a formula $\mathcal{A}$ is a Tautology we first negate the formula and then we verify if $\neg{A}$ is unsatisfiable.

How to check for a inference rule
Whenever we get to the conclusion we treat it like a tautology by negating it and checking for unsatisfiability

`xor` is a valid operator meaning $\wedge\neg$

`(push) - (pop)` are used to retract assertions