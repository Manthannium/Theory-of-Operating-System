# File Storage & Chained Allocation
Rules
```
Every block has 4 letters = 3 data and 1 pointer to next block, 
_ means NULL value, z means end pointer
Each block should have atleast 2 and atmost 3 data letters
When only 1 data letter, then adjust load with neighbour
You can modify atmost 2 blocks during insertion and deletion

After operation - 
If overloading  then split
If underloading then merge/shift
```
Representation of file random.txt
```
File : random.txt
Logical Representation  : qwertyuiop
Physical Representation : qwe,rt,yu,iop
a:qwes
s:rt_d 
d:yu_f
f:iopz
```
Insertion operations
```
// insert j as 6th letter (counting from 1) given free block g
qwe,rt,yu,iop -> qwe,rtj,yu,iop

// insert m as 5th letter
qwe,rtj,yu,iop -> qwe,rmtj,yu,iop
```
