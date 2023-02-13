# Round Robin
```
There is fixed quantum k say. We maintain queue.
Each process runs for k or less (if completes) according to queue.
New processes are inserted at the end of queue.
If there is no process in queue then current process is re-executed for k quantum
Disadvantage of RR is context switching time between process
```
Examples
```
Quantum = 10
Job   Ready   Service   RR
A     5       22        5-15, 25-35, 44-46
B     7       14        15-25, 40-44
C     19      5         35-40

t=5     Q:A
t=7     Q:B
t=15    Q:A
t=19    Q:A,C
t=25    Q:C,B
```

# Multilevel feedback queue (MLFQ)
```
It is extension of RR. here also quantums are there and process exectues cyclically
Here we have two queues - Low and High priority
High priority queue has smaller quantum than Low priority queue
New processes are send to HPQ and once pre-empted then send to LPQ

Extension - 
When new process comes in (HPQ), then running process (if from LPQ) then its preempted
even though the quantum is not completed
```
Examples
```
Quantum : 5(H),20(L). Don't use extension

Job Arrival Service Interval
A   0       60      0-5,    10-30,40-60,85-100
B   3       5       5-10
C   14      30      30-35   60-80,100-105
D   17      10      35-40   80-85
wait = 40+2+61+58 = 161

Same question with extension : HP can preempt LP between the quantum
Job Arrival Service Interval
A   0       60      0-5,   10-14, 24-44, 69-89, 94-105
B   3       5       5-10
C   14      30      14-19, 44-64, 89-94
D   17      10      19-24, 64-69
wait = 45+2+50+42 = 139 (much better than above)
```
Variant
```
Due to frequent context switching, 
we now allow LP turned HP process to use LP quantum till no new process comes.
This way the last came new (HP) process enjoys the quantum of LP, 
But since now it has become LP it can be preempted anytime by new HP. 
```
```
Quantum : 3,10

Job Ready  Service   Interval
P     0     20       0-5  18-19, 49-54
Q     5     20       5-8  29-39, 64-71
R     7     20       8-18 39-49
S    19     20       19-29, 54-64 

Job Ready Service Interval
A    0     20      0-3,18-28,33-40
B    1      8      3-8,28-31
C    8     12      8-18,31-33
```
MLFQ summary of various methods 
```
1. RR with LP and HP quantums
2. Above + HP can preempt LP before quantum
3. Above + HP enjoys LP quantum till new HP preempts it
```
