**[Day 4: Printing Department](https://adventofcode.com/2025/day/4)**

_(Input expected in A:A)_

**Part 1**

```py
=ARRAYFORMULA(LET(
   m,N(MID(TOCOL(A:A,1),SEQUENCE(1,140),1)="@"),
   G,LAMBDA(r,c,IFNA(INDEX(m,r,c))),
   J,LAMBDA(r,c,COUNTIF(
     {
       IF(OR(r=1,c=1),,G(r-1,c-1));
       IF(r=1,,G(r-1,c));
       IF(r=1,,G(r-1,c+1));
       IF(c=1,,G(r,c-1));G(r,c+1);
       IF(c=1,,G(r+1,c-1));
       G(r+1,c);
       G(r+1,c+1)
     },
     1)),
   c,SPLIT(TOCOL(IF(m,SEQUENCE(140)&","&SEQUENCE(1,140),),1),","),
   REDUCE(,SEQUENCE(ROWS(c)),LAMBDA(a,i,
     a+(J(INDEX(c,i,1),INDEX(c,i,2))<4)
   ))
))
```
