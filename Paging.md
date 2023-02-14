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
Example : page size = 2 variables
```
Disk a=59 b=87 c=89 d=28 e=81 f=72 g=83 h=74 i=62 j=54
Paging: [a,b Page p][c,d Page q][e,f Page r][g,h Page s][i,j Page t]
Disk p=2387 q=8928 r=8172 s=8384 t=3854

m=uvwxy means RAM value of the first variable of page m is vw second variable is xy. 
u=0 means these values are wrong on RAM and correct on Disk.
u=1 means these values are correct both on Disk and RAM.
u=2 means the value of only first variable is correct on RAM and wrong on Disk.
    i.e RAM holds correct value of first variable and disk holds correct value of second variable.
u=3 means Second variable correct on RAM (but wrong on disc). First variable correct on Disk.
u=4 means both values correct on RAM. At least one value wrong on Disk.

Initial Disk p=2387  q=8928  r=8172  s=8384  t=3854
Initial  RAM p=04568 q=08245 r=07363 s=08228 t=04332

print(d)     p=04568 q=18928 r=07363 s=08228 t=04332  8928 Disk->RAM
print(g)     p=04568 q=18928 r=07363 s=18384 t=04332  8384 Disk->RAM
print(c)     Same
h=48         p=04568 q=18928 r=07363 s=48348 t=04332  No transfer
print(d)     Same
a=59         p=25968 q=18928 r=07363 s=48348 t=04332  No transfer
print(h)     Same
print(b)     p=45987 q=18928 r=07363 s=48348 t=04332  2387 Disk->RAM cpu forms 5987 using 5968 and 2387
h=74         p=45987 q=18928 r=07363 s=48374 t=04332  No transfer
i=62         p=45987 q=18928 r=07363 s=48374 t=26232  No transfer
Over         Those pages where u is 2,3,4 are updated.
5987 and 8374 are RAM->Disk.
3854 is Disk->RAM. 6232 and 3854 is made as 6254. It is RAM->Disk.
Hence new disk is p=5987 q=8928 r=8172 s=8374 t=6254
```


Replacement Algorithms
```
FIFO, LFU, LRU
```
