**[Day 3: Lobby](https://adventofcode.com/2025/day/3)**

_(Input expected in A:A)_

**Part 1 & 2**

```py
=MAP({2;12},LAMBDA(k,
   SUM(MAP(TOCOL(A:A,1),LAMBDA(a,LET(
     c,100,
     s,SEQUENCE(c),
     0+REDUCE(
         LAMBDA(i,CHOOSE(i,TOCOL(,1),,1,c-k)),
         SEQUENCE(k),
         LAMBDA(T,_,LET(
           v,SORTN(VLOOKUP(
               SEQUENCE(T(4)-T(3)+2,1,T(3)),
               {s,MID(a,s,1)},{1,2}
           ),1,,2,),
           LAMBDA(i,CHOOSE(i,
             INDEX(v,1),
             T(2)&INDEX(v,2),
             1+INDEX(v,1),
             1+T(4)
           ))
     )))(2)
   ))))
))
``` 
