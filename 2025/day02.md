**[Day 2: Gift Shop](https://adventofcode.com/2025/day/2)**

_(Input expected in A1)_

**Part 1 & 2**

```py
=ARRAYFORMULA(LET(
   r,WRAPROWS(SPLIT(A1,"-,"),2),
   a,REPT(ROW(1:99999),2),
   i,UNIQUE(TOCOL(VSTACK(
        a,
        REPT(ROW(1:9999),2),
        REPT(ROW(1:999),{2,3}),
        REPT(ROW(1:99),{2,3,4,5}),
        REPT(ROW(1:9),{2,3,4,5,6,7,8,9,10})
   ),3)),
   MAP({0;1},LAMBDA(b,LET(
     z,--IF(b,i,a),
     SUMPRODUCT(
       z,
       BYROW(IF(z>=TOROW(INDEX(r,,1)),z<=TOROW(INDEX(r,,2))),LAMBDA(r,OR(r)))
     )
   )))
))
```
