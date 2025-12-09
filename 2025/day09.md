**[Day 9: Movie Theater](https://adventofcode.com/2025/day/9)**

_(Input expected in A:A)_

**Part 1 & 2**

```py
=ARRAYFORMULA(LET(
   a, TOCOL(A:A, 1),
   n, ROWS(a),
   c, SPLIT(a, ","),
   x, INDEX(c,,1),
   y, INDEX(c,,2),
   wxs, x,
   wys, y,
   wxe, {QUERY(x, "offset 1"); INDEX(x, 1)},
   wye, {QUERY(y, "offset 1"); INDEX(y, 1)},
   wl, IF(wxs < wxe, wxs, wxe),
   wt, IF(wys < wye, wys, wye),
   wr, IF(wxs > wxe, wxs, wxe),
   wb, IF(wys > wye, wys, wye),
   s, SEQUENCE(n),
   m, s < TOROW(s),
   tx, TOROW(x),
   ty, TOROW(y),
   cx, x < tx,
   cy, y < ty, 
   rl, TOCOL(IFS(m, IF(cx, x, tx)), 3),
   rt, TOCOL(IFS(m, IF(cy, y, ty)), 3),
   rr, TOCOL(IFS(m, IF(cx, tx, x)), 3),
   rb, TOCOL(IFS(m, IF(cy, ty, y)), 3),
   ok, REDUCE(0 * SEQUENCE(ROWS(rl)), s, LAMBDA(ko, i, 
         ko + 
           (INDEX(wl, i) < rr) * 
           (INDEX(wt, i) < rb) * 
           (INDEX(wr, i) > rl) * 
           (INDEX(wb, i) > rt)

   )) = 0,
   ar, (rr - rl + 1) * (rb - rt + 1),
   {MAX(ar); MAX(ok * ar)}
))
```
