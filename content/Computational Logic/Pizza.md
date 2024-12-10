
+++
title = 'Exercise: In pizzeria'
date = 2024-12-10
draft = false
math=true
+++
# In pizzeria
Exercise on <a href ='https://drive.google.com/drive/u/1/folders/1kL-sjIOiib0rL_7T1OGVIvJnYWH2_Jnh'>Drive</a> <br>
The customers have been named from a to f, starting from the top left




```
(declare-const a Real)
(declare-const b Real)
(declare-const c Real)
(declare-const d Real)
(declare-const e Real)
(declare-const f Real)
(assert(= (+ a b) (+ e f)))
(assert(< b a))
(assert(or (= c 9.5)(= c 7.5)(= c 8.5)(= c 7)))
(assert(or (= d 9)(= d 9.5)))
(assert(or (= e 9)(= e 9.5)))
(assert(or (= f 9)(= f 7)))
(assert(or (= a 9.5)(= a 7.5)(= a 8.5)(= a 7)(= a 8)(= a 9)))
(assert(or (= b 9.5)(= b 7.5)(= b 8.5)(= b 7)(= b 8)(= b 9)))
(assert(distinct a b c d e f))
(check-sat)
(get-value(a b c d e f))
```