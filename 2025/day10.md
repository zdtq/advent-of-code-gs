**[Day 10: Factory](https://adventofcode.com/2025/day/10)**

_(Input expected in A:A)_

**Part 1**

```py
=ARRAYFORMULA(REDUCE(0, TOCOL(A:A, 1), LAMBDA(r, a, r + LET(
   p, SPLIT(REGEXREPLACE(a, "{.*",), "[]() "),
   d, INDEX(p,,1),
   i, SEQUENCE(LEN(d)) - 1,
   t, SUM((MID(d, i+1, 1) = "#") * (2 ^ i)),    
   b, CHOOSECOLS(p, SEQUENCE(COLUMNS(p) - 1, 1, 2)),
   sm, SPLIT(TOCOL(b), ","),
   m, MMULT((sm <> "") * 2^sm, SEQUENCE(COLUMNS(sm)) ^ 0),
   BFS, LAMBDA(BFS, c, s, v,
     IF(OR(t=c), s,
       LET(
         n, TOCOL(BITXOR(c, TOROW(m))),
         nv, UNIQUE(FILTER(n, ISNA(XMATCH(n, v)))),
         BFS(BFS, nv, s+1, {v; nv})
       )
     )
   ),
   BFS(BFS, 0, 0, 0)
))))
```
