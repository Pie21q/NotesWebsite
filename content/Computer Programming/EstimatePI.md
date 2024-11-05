+++
title = 'Estimate PI'
date = 2024-11-05
draft = false
math = true
+++
$$\frac{1}{\pi} = \frac{2\sqrt{2}}{9801} \sum_{k=0}^\infty \frac{(4k)!(1103+26390k)}{(k!)^4396^{4k}}$$

Estimate Pi using the formula above, then compare it with math.pi
```
import math as m
def estimatePi():
    t = 0 #  t is last term
    k = 0
    while t < 1e-15:
        t = t + ((m.factorial(4*k)) * 1103 + 26390 * k) / (pow((m.factorial(k)), 4) * pow(396, 4 *k))
        k = k + 1
    return (2 * m.sqrt(2) ) / 9801 * t

print(1/ estimatePi())
print(m.pi)
```