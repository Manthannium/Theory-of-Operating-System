# Memory Partition
Static Partition (fixed sized discrete blocks) and Dynamic Partition (Continuous memory allocation)

### Memory allocation strategies
```
Best Fit Available (BFA)
- allocate the block with smallest memory >= required among the available (free) blocks
- logical strategy but creates small holes that are sometimes hard to fill

Best Fit Only (BFO)
- here best fit is chosen among all the blocks whether free or available 

First Fit (FF)
- allocate the first block that fits the need
- easy to implement, time efficient, but no logic

Worst Fit (WF)
- allocate biggest sized block available
- avoid small holes

Generally,
In Static Partition, we use BFA and BFO
In Dynamic, we use BFA, BFO, FF, WF
However, we can do whatever we want
```

### Static Partition
```
Discrete Blocks of Fixed size are avaiable in memory
Either full or no allocation can be done. Partial allocation or Merging of blocks is not allowed.
Static partition causes fragmentation (waste of memory)
```
Internal Fragmentation
```
It is caused by job which has lower memory need that alloted. Thus forming holes
```
External Fragmentation
```
It is felt to unalloted job iff sum of available memory > required memory
```
Examples
```
Memory blocks P:80, Q:60, R:40, S:20, T:10 using Best fit Available

Job   Need  Action  IF  EF  Reason
A     76    P       4   0
B     19    S       1   0
C     66    wait    0   110 (60+40+10 > 66)
D     56    Q       4   0
E     55    wait    0   0   (40+10 < 55)
F     42    wait    0   50  (40+10 > 42)

Memory blocks P:50, Q:60, R:20, S:30 . Job A,B,C demand 46,12,34

BFA : A:P, B:R, C:Q
BFO : A:P, B:R, C:wait for P
FF  : A:P, B:Q, C:wait
WF  : A:Q, B:P, C:wait
```

### Dynamic Partition
````
In dynamic partition there is no internal or external fragmentation.
````
