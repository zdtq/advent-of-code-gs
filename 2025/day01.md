**[Day 1: Secret Entrance](https://adventofcode.com/2025/day/1)**

_(Input expected in A:A)_

**Part 1 & 2**

```py
=SORT(LET(
  c,100,
  m,IF(LEFT(A:A)="L",-1,1)*MID(A:A,2,9),
  e,SCAN(50,m,LAMBDA(a,b,MOD(a+b,c))),
  i,MOD(e-m,c),
  {
   SUM(N(e=0));
   SUM(1+INT((ABS(m)-IF(i=0,c,IF(SIGN(m)=1,c-i,i)))/c))
  }
))
```
