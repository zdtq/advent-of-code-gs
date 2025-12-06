**[Day 6: Trash Compactor](https://adventofcode.com/2025/day/6)**

_(Input expected in A1)_

**Part 1 & 2**

```py
=ARRAYFORMULA(BYCOL(LET(
   p,TOCOL(SPLIT(A1,CHAR(10))),
   op,CHOOSEROWS(p,-1),
   s,SEQUENCE(LEN(op)),
   a,TOCOL(IF(REGEXMATCH(MID(op,s,1),"[+*]"),s,),1),
   b,IFNA(HSTACK(
       a,
       QUERY(a-2,"offset 1",),
       TOCOL(SPLIT(op," "))
   ),MAX(a)+3),
   MAP(INDEX(b,,1),INDEX(b,,2),INDEX(b,,3),LAMBDA(s,e,o,LET(
     x,MID(CHOOSEROWS(p,SEQUENCE(ROWS(p)-1)),SEQUENCE(1,e-s+1,s),1),
     y,--BYROW(x,LAMBDA(r,JOIN(,r))),
     z,--BYCOL(x,LAMBDA(c,JOIN(,c))),
     IF(o="+",{SUM(y),SUM(z)},{PRODUCT(y),PRODUCT(z)})
   )))
 ),LAMBDA(c,SUM(c))))
```
