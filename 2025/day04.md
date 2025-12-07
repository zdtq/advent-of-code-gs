**[Day 4: Printing Department](https://adventofcode.com/2025/day/4)**

_(Input expected in A1)_

**Part 1**

```py
=ARRAYFORMULA(LET(
  i, SUBSTITUTE(A1, CHAR(10), ),
  l, LEN(i),
  w, l^0.5,
  k, ROW(1:8)^0,
  s, SEQUENCE(l),
  m, N(MID(i, s, 1)="@"),
  x, s + {-w-1, -w, -w+1, -1, 1, w-1, w, w+1},
  h, TOCOL(IF((x<1) + (x>l) + (ABS(MOD(x-1, w) - MOD(s-1, w)) > 1), l+1, x)), 
  {
    SUM(m * (MMULT(WRAPROWS(CHOOSEROWS({m;0}, h), 8), k)<4));
    SUM(m) - SUM(REDUCE(m, SEQUENCE(75), LAMBDA(a, _,
       IF(MMULT(WRAPROWS(CHOOSEROWS({a; 0}, h), 8), k) < 4, 0, a)
    )))
  }
))
```
