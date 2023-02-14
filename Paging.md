# Demand paging
```
RAM is limited memory so everything is stored in Disc
Whenever need arises those variables / pages are brought to RAM from Disc
We try to minimize things brought to RAM
```
Example : Without paging or say page size = 1 variable
```
k=xyz means value of variable k is yz on RAM. 
x=0 means RAM value is wrong. Disk value is correct.
x=1 means both values are correct.
x=2 means RAM value is correct. Disk value is wrong.

Initial​Disk a=23 b=87 c=89 d=28 e=81 f=72 g=83 h=84 i=38 j=54
Initial RAM  a=045 b=068 c=082 d=045 e=073 f=063 g=082 h=028 i=043 j=032

print(d)    a=045 b=068 c=082 d=128 e=073 f=063 g=082 h=028 i=043 j=032   28 Disk->RAM
print(g)    a=045 b=068 c=082 d=128 e=073 f=063 g=183 h=028 i=043 j=032   83 Disk->RAM
print(c)    a=045 b=068 c=189 d=128 e=073 f=063 g=183 h=028 i=043 j=032   89 Disk->RAM
h=48        a=045 b=068 c=189 d=128 e=073 f=063 g=183 h=248 i=043 j=032   No Transfer
print(d)    Same
a=59        a=259 b=068 c=189 d=128 e=073 f=063 g=183 h=248 i=043 j=032   No Transfer
print(h)    Same
print(b)    a=259 b=187 c=189 d=128 e=073 f=063 g=183 h=248 i=043 j=032   87 Disk->RAM 
h=74        a=259 b=187 c=189 d=128 e=073 f=063 g=183 h=274 i=043 j=032   No transfer
i=62        a=259 b=187 c=189 d=128 e=073 f=063 g=183 h=274 i=262 j=032   No transfer

Over Those variables where x is 2 are updated.
59,74 and 62 are trasfered RAM->Disk
Observe here that in print instruction, we need the variable value hence it is brought from Disk
But in updating the variable we don't require its old value so no transfer takes place.
We always try to minmize the variable brought to RAM (due to limited storage)
```


Replacement Algorithms
```
FIFO, LFU, LRU
```
