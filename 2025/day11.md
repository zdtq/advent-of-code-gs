**[Day 11: Reactor](https://adventofcode.com/2025/day/11)**

_(Input expected in A:A)_

**Part 1**

```py
=ARRAYFORMULA(LET(
   a, TOCOL(A:A, 1),
   s, SPLIT(a, ":"),
   k, INDEX(s,,1),
   v, INDEX(s,,2),
   C, LAMBDA(C, s, IF(s = "out", 1, LET(
        e, XLOOKUP(s, k, v,),
        IF(e = "", 0, SUM(
          MAP(SPLIT(e, " "), LAMBDA(e, C(C, e)))
        ))
   ))),
   C(C, "you")
))
```
