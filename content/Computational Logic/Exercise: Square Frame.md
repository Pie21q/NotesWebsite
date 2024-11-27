+++
title = 'Exercise: Square Frame'
date = 2024-11-27
draft = false
math=true
+++
You are given the following 10 tiles:
[1 | 3] , [6 | 1] , [3 | 2] , [9 | 6] ,
[1 | 2] , [4 | 9] , [2 | 6] , [2 | 4] , [6 | 1] , [2 | 2].

Each tile has two cells, with numbers printed inside them. Arrange the tiles in a square frame
(’cornice quadrata’) in such a way that two adjacent cells have the sa-
me number (or show that no such arrangement exists). [Hint: use the
declare-datatypes utility to declare the 10-members set comprising your
tiles. Then introduce two Int-valued functions representing the content of
the left and the right cells. Use a further Int-valued function to formalize
the position (from 1 to 10) of each tile in the solution frame.]


```
(declare-datatypes () (( Tiles a b c d e f g h i j)))
(declare-fun Left(Tiles) Int)
(declare-fun Right(Tiles) Int)
(declare-fun Position(Tiles) Int )
(assert(= (Left a) 1))
(assert(= (Right a) 3))
(assert(= (Left b) 6))
(assert(= (Right b) 1))
(assert(= (Left c) 3))
(assert(= (Right c) 2))
(assert(= (Left d) 9))
(assert(= (Right d) 6))
(assert(= (Left e) 1))
(assert(= (Right e) 2))
(assert(= (Left f) 4))
(assert(= (Right f) 9))
(assert(= (Left g) 2))
(assert(= (Right g) 6))
(assert(= (Left h) 2))
(assert(= (Right h) 4))
(assert(= (Left i) 6))
(assert(= (Right i) 1))
(assert(= (Left j) 2))
(assert(= (Right j) 2))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 0) (=(Position y)1) (=(Right x)(Left y)))))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 1) (=(Position y)2) (=(Right x)(Left y)))))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 2) (=(Position y)3) (=(Right x)(Left y)))))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 3) (=(Position y)4) (=(Right x)(Left y)))))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 4) (=(Position y)5) (=(Right x)(Left y)))))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 5) (=(Position y)6) (=(Right x)(Left y)))))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 6) (=(Position y)7) (=(Right x)(Left y)))))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 7) (=(Position y)8) (=(Right x)(Left y)))))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 8) (=(Position y)9) (=(Right x)(Left y)))))
(assert(exists ((x Tiles)(y Tiles))  (and (=(Position x) 9) (=(Position y)0) (=(Left y)(Right x)))))
(check-sat)
(get-value((Position a)(Position b)(Position c)(Position d)(Position e)(Position f)(Position g)(Position h)(Position i)(Position j)))
```