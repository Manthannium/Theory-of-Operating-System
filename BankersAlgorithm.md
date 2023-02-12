# Banker's Algorithm for Deadlock avoidance (dynamic)

```
Cuurently available 15
Process  Given  additional Need
G        20      17
H        30      20
K        4       7

At most 8 can be given to G. Then K,G,H be fulfilled  (If 9 are given to G. Now 6 are available. No process can be done.)
At most 2 can be given to H. Then K,G,H 
(If 3 are given to H. 12 available. K can be done. Now 12+4=16 available. Now nothing can be done) 
```
```
Available = 20. Find max amount that can be given to jobs
Job   Given   Needed
A     4         12
B     6         18
C     20        27
D     5         49

Max 12 to A, then BCD
Max 18 to B, then ACD
Max 6 to C, then ABCD
Max 3 to D, then ABCD
```
```
Available = 20. Find max amount that can be given to jobs
Job   Given   Needed
A     4         12
B     6         18
C     20        24
D     5         49

Max 12 to A, then BCD
Max 18 to B, then (ACD or CAD)
Max 8 to C, then ACBD
Max 6 to D, then ABCD
```
