**[Day 7: Laboratories](https://adventofcode.com/2025/day/7)**

_(Input expected in A:A)_

**Part 1 & 2**

```py
=ARRAYFORMULA(LET(
   f, A1,
   r, TOCOL(A2:A,1),
   w, LEN(f),
   O, REDUCE(
        LAMBDA(i, CHOOSE(i, 0, N(MID(A1, SEQUENCE(1, w), 1) = "S"))),
        r,
        LAMBDA(C, r, LET(
          sp, N(MID(r, SEQUENCE(1, w), 1) = "^"),
          bp, (1-sp) * C(2), 
          bl, {0, CHOOSECOLS(sp * C(2), SEQUENCE(1, w - 1))},
          br, {CHOOSECOLS(sp*C(2), SEQUENCE(1, w - 1, 2)), 0},
          LAMBDA(i, CHOOSE(i, C(1) + SUM(sp * (C(2)>0)), bp+bl+br))
        ))
   ),
   {O(1); SUM(O(2))}
))
```
