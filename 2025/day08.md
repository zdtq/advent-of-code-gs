**[Day 8: Playground](https://adventofcode.com/2025/day/8)**

_(Input expected in A:A)_

**Part 1 & 2**

```py
=ARRAYFORMULA(LET(
   a, TOCOL(A:A, 1),
   n, ROWS(a),
   s, SEQUENCE(n),
   c, SPLIT(a, ","),
   x, INDEX(c,,1),
   y, INDEX(c,,2),
   z, INDEX(c,,3),
   d, (x - TOROW(x))^2 + (y - TOROW(y))^2 + (z - TOROW(z))^2,
   m, s < TOROW(s),
   fd,  TOCOL(IF(m, d,), 1),
   ba, TOCOL(IF(m, s,), 1),
   bb, TOCOL(IF(m, TOROW(s),), 1),  
   sd, SORTN({fd, ba, bb}, 10000, , 1, 1),  
   TOCOL(INDEX(REDUCE(HSTACK(s, s^0, {0; 0}), SEQUENCE(ROWS(sd)), LAMBDA(cs, i,
      IF(INDEX(cs, 2, 3), cs, LET(
        g, INDEX(cs,,1),
        z, INDEX(cs,,2),
        ba, INDEX(sd, i, 2),
        bb, INDEX(sd, i, 3),
        ga, INDEX(g, ba),
        gb, INDEX(g, bb),
        IF(ga=gb, cs, LET(
          nz, INDEX(z, ba) + INDEX(z, bb),
          pa, IF(i=1000, PRODUCT(SORTN(z, 3, 2, 1,)), INDEX(cs, 1, 3)),
          pb, IF(nz=n, INDEX(x, ba) * INDEX(x, bb), 0),
          HSTACK( 
            IF(g=gb, ga, g), 
            IF((g=ga)+(g=gb), nz, z), 
            {pa; pb}
          )
        ))
      ))
  )),,3),3)
))
```
