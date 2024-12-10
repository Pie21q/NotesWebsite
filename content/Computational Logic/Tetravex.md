
+++
title = 'Exercise: Tetravex'
date = 2024-12-10
draft = false
math=true
+++
# Tetravex
Exercise on <a href ='https://drive.google.com/drive/u/1/folders/1kL-sjIOiib0rL_7T1OGVIvJnYWH2_Jnh'>Drive</a>
- Positions are named 0-8 starting from top left and ending bottom right
- Tiles are named from a to i

```
(declare-datatypes () (( Tiles a b c d e f g h i)))
(declare-fun Left(Tiles) Int)
(declare-fun Right(Tiles) Int)
(declare-fun Top(Tiles) Int)
(declare-fun Bot(Tiles) Int)
(declare-fun Position(Tiles) Int )
(assert(= (Left a) 3))
(assert(= (Right a) 8))
(assert(= (Top a) 3))
(assert(= (Bot a) 1))

(assert(= (Left b) 8))
(assert(= (Right b) 1))
(assert(= (Top b) 1))
(assert(= (Bot b) 6))

(assert(= (Left c) 3))
(assert(= (Right c) 8))
(assert(= (Top c) 0))
(assert(= (Bot c) 3))

(assert(= (Left d) 7))
(assert(= (Right d) 2))
(assert(= (Top d) 6))
(assert(= (Bot d) 6))

(assert(= (Left e) 2))
(assert(= (Right e) 5))
(assert(= (Top e) 4))
(assert(= (Bot e) 0))

(assert(= (Left f) 4))
(assert(= (Right f) 7))
(assert(= (Top f) 3))
(assert(= (Bot f) 5))

(assert(= (Left g) 5))
(assert(= (Right g) 3))
(assert(= (Top g) 9))
(assert(= (Bot g) 0))

(assert(= (Left h) 1))
(assert(= (Right h) 1))
(assert(= (Top h) 4))
(assert(= (Bot h) 4))


(assert(= (Left i) 8))
(assert(= (Right i) 8))
(assert(= (Top i) 4))
(assert(= (Bot i) 4))

(assert(exists ((x Tiles)(y Tiles)(z Tiles))  (and (=(Position x) 0) (=(Position y)1) (=(Right x)(Left y)) (=(Position z ) 3) (=(Bot x)(Top z))  )))
(assert(exists ((x Tiles)(y Tiles)(z Tiles))  (and (=(Position x) 1) (=(Position y)4) (=(Bot x)(Top y)) (=(Position z ) 2 ) (=(Right x)(Left z))  )))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 2) (=(Position y)5) (=(Bot x)(Top y)) )))
(assert(exists ((x Tiles)(y Tiles)(z Tiles))  (and (=(Position x) 3) (=(Position y)4) (=(Right x)(Left y)) (=(Position z ) 6 ) (=(Bot x)(Top z))  )))
(assert(exists ((x Tiles)(y Tiles)(z Tiles))  (and (=(Position x) 4) (=(Position y)7) (=(Bot x)(Top y)) (=(Position z ) 5 ) (=(Right x)(Left z))  )))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 5) (=(Position y)8) (=(Bot x)(Top y)) )))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 6) (=(Position y)7) (=(Right x)(Left y)) )))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 7) (=(Position y)8) (=(Right x)(Left y)) )))

(check-sat)
(get-value((Position a)(Position b)(Position c)(Position d)(Position e)(Position f)(Position g)(Position h)(Position i)))
```