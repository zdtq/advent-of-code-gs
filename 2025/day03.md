**[Day 3: Lobby](https://adventofcode.com/2025/day/3)**

_(Input expected in A:A)_

**Part 1 & 2**

```py
=MAP({2;12},LAMBDA(k,
   SUM(MAP(TOCOL(A:A,1),LAMBDA(a,LET(
     c,100,
     s,SEQUENCE(c),
     0+REDUCE(
         LAMBDA(i,CHOOSE(i,,1,c-k)),
         SEQUENCE(k),
         LAMBDA(T,_,LET(
           v,SORTN(VLOOKUP(
               SEQUENCE(T(3)-T(2)+2,1,T(2)),
               {s,MID(a,s,1)},{1,2}
           ),1,,2,),
           LAMBDA(i,CHOOSE(i,
             T(1)&INDEX(v,2),
             1+INDEX(v,1),
             1+T(3)
           ))
     )))(1)
   ))))
))
``` 
