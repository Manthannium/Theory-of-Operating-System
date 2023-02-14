# Table Fragmentation
```
During dynamic partition, we have many blocks of free memory
Storage of information regarding free space of memory in memory is called Table Fragmentation
```
Example
```
Job             A     B     C      D      E       F       G       H
Ready           0     1     3      4      5       6       7       9
Memory Need     8     5     10     10     8       15      10      33
Allocate        0-7   8-12  13-22  23-32  33-40   41-55   56-65   66-98
Service time    15    20    13     20     9       30      15      2
Run             0-15  1-21  3-16   4-24   5-14    6-36    7-22    9-11

Job             I       J
Ready           10      17
Memory Need     5       32
Allocate        66-70   ?
Service time    1
Run             11-12

at t=8, memory 66-99 was free
at t=17, memory 0-7,13-22,33-40,66-99 is free

But these free slots (their start and end location) are stored at the end of memory
M99 = 33-40
M98 = 0-7
M97 = 13-22
M96 = 66-96

Thus last 4 location are occupied storing information about free slots
So when J comes at t=17, it sees 66-96 = 31 units of free space 
So J can't be alloted space even though there is space but has got wasted in storing free spaces
Because of Table Fragmentation, job J is kept waiting
```
Information regarding free slots can be stored in many ways. Instead of storing all information at the end (96-99) is not good strategy.
Instead of that,we can store information at the end of every free slots and these free slots are linked in chain like fashion
```
Format 1 : (start of this, end of next)

t=8,  M99 = 66,_
t=10  M99 = 99,_
t=13, M99 = 66,_
t=14, M99 = 66,40  (66-99 free)
      M40 = 33,_   (33-40 free)
t=15, M99 = 66,40  (66-99)
      M40 = 33,7   (33-40)
      M07 = 0,_    (0-7)
t=16, M99 = 66,40  
      M40 = 33,7
      M07 = 0,22
      M22 = 13,_
      
_ means NULL pointer (no next slot)
next pointer helps in reaching the location of next free slot
Just like linked list

t=17, Job J arrives (demands 32 units memory)
      M99 = 98,40  (66-97 is alloted to J, thus free is 98-99)
      M40 = 33,7
      M07 = 0,22
      M22 = 13,_
      
lets say t=19, 9 units reqiured
so allot 13-21 to it
      M99 = 98,40  
      M40 = 33,7
      M07 = 0,22
      M22 = 22,_ 
      
t=20, 8 units required, give 33-40
      M99 = 98,07  
      M07 = 0,22
      M22 = 22,_ 
Thus updation of info is like linked list
```
Example 2
```
Format : (start of this, end of next)
Given free slots of memory below
95-99       M99 = 95,31
19-31       M31 = 19,45
42-45       M45 = 42,68
60,68       M68 = 60,51
49,51       M51 = 49,12
8-12        M12 = 8,_

Now below are new free blocks, show blocks that changes in memory
55-58       M99 = 95,58
            M58 = 55,31
55-59       M68 = 55,51 (as continuos block from 55-68)
69-72       M45 = 42,72
            M72 = 60,51 (erase M68)
46-48       M31 = 19,68
            M68 = 60,51
            M51 = 42,12
```
