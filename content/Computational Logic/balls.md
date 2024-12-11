
+++
title = 'Exercise: Ball'
date = 2024-12-11
draft = false
math=true
+++

```
(define-fun PRE ((b Int) (w Int)) Bool (and (= b 9) (= w 10)))
(define-fun POST   ((b Int) (w Int)) Bool (and (= b 1) (= w 0)))

(define-fun TRANS 
            ((b Int) (w Int) (bp Int) (wp Int)) Bool
             (and (<= 0 bp) (<= 0 wp)
              (or 
                 (and (= bp ( + b 1))(= wp (- w  2)))
                 (= bp (- b 1))
                 (= bp (- b 1))
              )
             )
            )  



(declare-const x0 Int )
(declare-const y0 Int)


(declare-const x1 Int )
(declare-const y1 Int)

(declare-const x2 Int )
(declare-const y2 Int)

(declare-const x3 Int )
(declare-const y3 Int)

(declare-const x4 Int )
(declare-const y4 Int)


(declare-const x5 Int )
(declare-const y5 Int)


(declare-const x6 Int )
(declare-const y6 Int)


(declare-const x7 Int )
(declare-const y7 Int)


(declare-const x8 Int )
(declare-const y8 Int)


(declare-const x9 Int )
(declare-const y9 Int)


(declare-const x10 Int )
(declare-const y10 Int)


(declare-const x11 Int )
(declare-const y11 Int)


(declare-const x12 Int )
(declare-const y12 Int)

(declare-const x13 Int )
(declare-const y13 Int)

(declare-const x14 Int )
(declare-const y14 Int)

(declare-const x15 Int )
(declare-const y15 Int)

(declare-const x16 Int )
(declare-const y16 Int)

(declare-const x17 Int )
(declare-const y17 Int)

(declare-const x18 Int )
(declare-const y18 Int)

(declare-const x19 Int )
(declare-const y19 Int)

(declare-const x20 Int )
(declare-const y20 Int)

(declare-const x21 Int )
(declare-const y21 Int)

(declare-const x22 Int )
(declare-const y22 Int)

(declare-const x23 Int )
(declare-const y23 Int)

(declare-const x24 Int )
(declare-const y24 Int)

(declare-const x25 Int )
(declare-const y25 Int)



(assert (PRE x0 y0 ) )


(assert (TRANS x0 y0 x1 y1 ) )
(assert (TRANS x1 y1 x2 y2 ) )
(assert (TRANS x2 y2 x3 y3 ) )
(assert (TRANS x3 y3 x4 y4 ) )
(assert (TRANS x4 y4 x5 y5 ) )
(assert (TRANS x5 y5 x6 y6 ) )
(assert (TRANS x6 y6 x7 y7 ) )
(assert (TRANS x7 y7 x8 y8 ) )
(assert (TRANS x8 y8 x9 y9 ) )
(assert (TRANS x9 y9 x10 y10 ) )








(assert (POST x10 y10 ) )



(check-sat)

(echo " ")
(echo "step 0")
(eval x0)
(eval y0)
(echo " ")
(echo "step 1")
(eval x1)
(eval y1)
(echo " ")
(echo "step 2")
(eval x2)
(eval y2)
(echo " ")
(echo "step 3")
(eval x3)
(eval y3)
(echo " ")
(echo "step 4")
(eval x4)
(eval y4)
(echo " ")
(echo "step 5")
(eval x5)
(eval y5)
(echo " ")
(echo "step 6")



(eval x6)
(eval y6)

(echo " ")
(echo "step 10")



(eval x10)
(eval y10)
```