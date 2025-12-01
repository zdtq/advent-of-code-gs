**[Day 1: Secret Entrance](https://adventofcode.com/2025/day/1)**

_(Input expected in A:A)_

**Part 1 & 2**

```py
=SORT(LET(
  c,100,
  raw,TOCOL(A:A,1),
  m,IF(LEFT(raw)="L",-1,1)*MID(raw,2,99),
  e,SCAN(50,m,LAMBDA(a,b,MOD(a+b,c))),
  i,MOD(e-m,c),
  d,IF(i=0,c,IF(SIGN(m)=1,c-i,i)),
  {
   SUM(N(e=0));
   SUM(1+INT((ABS(m)-d)/c))
  }
))
```
