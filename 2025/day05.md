**[Day 5: Cafeteria](https://adventofcode.com/2025/day/5)**

_(Input expected in A:A)_

**Part 1 & 2**

```py
=ARRAYFORMULA(LET(
   x,TOCOL(A:A,1),
   m,REGEXMATCH(x&"","-"),
   r,SPLIT(FILTER(x,m),"-"),
   i,FILTER(x,1-m),
   s,SORT(r),
   {
    N("Part 1")+
    SUM(BYCOL(
      (TOROW(i)>=INDEX(r,,1))*(TOROW(i)<=INDEX(r,,2)),
      LAMBDA(c,--OR(c))
    ));
    N("Part 2")+
    SUM(QUERY(
      REDUCE(INDEX(s,1),SEQUENCE(ROWS(s)),LAMBDA(a,c,LET(
        cs,INDEX(s,c,1),
        ce,INDEX(s,c,2),
        ls,INDEX(CHOOSEROWS(a,-1),,1),
        le,INDEX(CHOOSEROWS(a,-1),,2),
        IF(cs<=le,
          VSTACK(CHOOSEROWS(a,SEQUENCE(ROWS(a)-1)),{ls,MAX(le,ce)}),
          VSTACK(a,{cs,ce})
        )
    ))),"select Col2-Col1+1"
    ))
   }
))
```
