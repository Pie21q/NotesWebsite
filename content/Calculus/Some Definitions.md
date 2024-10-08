+++
title = 'Some Definitions'
date = 2024-10-08
draft = false
math = true
+++
Bounded and unbounded Sets
$Q \supseteq A \rightarrow where \ A \{2,3\}, if \ exists \ a \ number \ such \ that \ 2<r \in Q <3, then \ A \ is \ a \ bounded  \ set$
Q couldn't be a bounded set as  $Q = \{-\infty, +\infty\}$

A Set can be bounded below, such that  $A = \{0, +\infty \}$, A Set can also be upwards bounded, such that$A = \{-\infty, 2 \}$

Any non empty subset of $\mathbb{R}$ has a sup and a inf

Considering $A = \{-1, 5\}$ then $-A = \{x \in \mathbb{R} -x\in A \}$   
so $-(-1,5) = (-5,1)$ 
we can say that $sup(-A) = -inf\ A$ and $inf(-A) = -sup\ A$

In $R$ most things are defined, such as $\log A$ or $\cos(\alpha)$ , but we still cant divide by 0 or solve $\sqrt{-2}$ as $A^\alpha > 0$ 

Formula to solve third degree equations such as $X^3 + px = q$
$$x = \sqrt[3]{A + \sqrt{B}} \ + \sqrt[3]{A - \sqrt{B}}  $$
Accepting complex numbers means accepting the fact that the numbers are in an **Unordered Field**
$\mathbb{C}$ field must $\mathbb{C} \supseteq \mathbb{R}$    

We can represent complex numbers as a plane, where the X value is the real value and the Y value is the imaginary

## Operations
**Sum** is computed as the vector sum between the 2 points (You add together the Real part and the imaginary Part)

$2+3i + 3-4i = 5-1i$ 

### Multiplication
$$(x + iq)(v +iw) = xv + i(qv +xw) + qwi^2 = xv -qw +i(qv+xw),\ considering \ i^2 \ as \ -1$$
### Conjugation($\bar{A}$)
conjugation refers to a pair of binomials that differ only by sign, in case of complex conjugation, the difference has to be in the imaginary part
$z = a +ib \ then \ \bar{z}= a - ib$  while $z=3 \ then \  \bar{z} = 3$
$z$ and $\bar{z}$ are symmetric in relation to the X axis, also $z \cdot \bar{z} = z^2$ 

### Reciprocal
$z = x + iy \neq 0$ 
$\frac{1}{z} = \frac{1}{x+iy}$ we then multiply for the conjugate giving $$\frac{x-iy}{x^2+y^2}=\frac{x}{x^2 + y^2} - \frac{y}{x^2-y^2}i$$
## Fundamental Theorem of Algebra
One of the strongest properties of $\mathbb{C}$ is the fact that it is algebraically closed $\rightarrow$ any polynomial of degree $\ge$ 1 `(pol. of degree 0 are costants)` with coefficient in $\mathbb{C}$ has a root in $\mathbb{C}$


## Computing Powers 
computing $(x + iy)^7$  normally would be very time expensive 

We can use a different approach based on geometry

![[Excalidraw/Drawing 2024-10-08 09.51.13.excalidraw]]
$\tilde{z}$ is new object related to an original object $z$ 
### Trigonometric Representation of a Complex number
$$ z = \mid z \mid (\cos(\theta) +i\sin(\theta)) $$

knowing this, $z^n$ becomes, using `de moivre formula`
$$z^n = \mid z \mid (\cos n\theta + i\sin n\theta) $$