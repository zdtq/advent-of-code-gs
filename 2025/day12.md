**[Day 12: Christmas Tree Farm](https://adventofcode.com/2025/day/12)**

_(Input expected in A:A)_

```py
=ROWS(QUERY(
   FILTER(SPLIT(A:A, "x: "), FIND("x", A:A)),
   "where Col1*Col2/9 >= Col3+Col4+Col5+Col6+Col7+Col8"
))
```
