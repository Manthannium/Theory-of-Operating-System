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
Memory blocks P:80, Q:60, R:40, S:20, T:10 using Best fit available

Job   Need  Action  IF  EF
A     76    
Let Jobs A..F demand 76, 19, 66, 56, 55, 42 memory respectively. Write internal and external fragmentation at every stage.
```


### Dynamic Partition
````
In dynamic partition there is no internal or external fragmentation.
````
