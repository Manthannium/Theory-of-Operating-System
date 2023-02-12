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
Insertion
```
// insert j as 6th letter (counting from 1) given free block g
qwe,rt,yu,iop -> qwe,rtj,yu,iop

a:qwes
s:rtjd 
d:yu_f
f:iopz

// insert m as 5th letter
qwe,rtj,yu,iop -> qwe,rmtj,yu,iop (overload) -> qwe,rm,tj,yu,iop

a:qwes
s:rm_g (!) 
g:tj_d (!)
d:yu_f
f:iopz

(!) = modified blocks

// insert x as 8th letter
qwe,rm,tj,yu,iop -> qwe,rm,tj,xyu,iop

// insert m as 2nd letter in below text
abc,de -> ambc,de (over) -> am,bc,de   
In overloading we can't do shifting so amb,cde is WRONG
```
Deletion
```
// delete 4th letter
qwe,rm,tj,xyu,iop -> qwe,m,tj,xyu,iop (underload) -> qw,em,tj,xyu,iop / qwe,mtj,xyu,iop

// delete g
sxc,gh,if,dmt -> sxc,h,if,dmt (under) -> sx,ch,if,dmt / sxc,hif,dmt
```
