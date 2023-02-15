# Disc Scheduling
```
There is single server that can move from location 0 to 100
Jobs (Serve requests) arrives at specific location
It takes 0 time in serving and 1 unit of time in traversing 1 unit on disc
All the schedulings are non-pre-emptive. 
Assuming we have locations from L=0 to 100 and at t=0 out pointer/server is at L=0 
```
### 1. FCFS (First Come First Serve)
```
Pointer starts to move from L=0 when it sees first request
Serves the request according to their ready time. 

Advantage – naturally serve those who comes first
Disadvantage – more direction flips and path repetitions 
```
### 2. SSTF (Shortst Seek Time First)
```
Pointer starts to move from L=0 when it sees first request
Serves the request according to proximity. Request whose location is nearest to the pointer is served first. 
However, it first makes the decision and then moves. 
So even if some request come in the path but was not decided earlier then it won’t execute that.

Advantage – why should we seek much time in travelling? Lets do task that requires less travelling time. 
Useful in trip. When you go to some place, you try to visit nearby places. 
Disadvantage – more direction flips due to greediness of nearer location
```
### 3. SCAN (elevator scheduling)
```
Pointer starts to move from L=0 from t=0. It goes on moving even without any request
Its only target is to move from L=0 to L=100 to and fro and complete the request that comes in the path. 
It doesn’t change the direction in between.

Advantage – pointer doesn’t stop anywhere. Goes on swinging and completes task in path thus avoiding path repetitions
Disadvantage – Goes to L=100 and L=0 even though there is no request over there. Redundant travelling
```
### 4. LOOK
```
Pointer starts to move from L=0 when it sees first request but is smarter than SCAN
It completes the requests that come in the path
When no further request then changes the direction

Advantage – smarter than SCAN, completes task in path, only goes till last request and thus avoiding path repetitions
Disadvantage - none (its best algo)
```
|FCFS	|SSTF|	SCAN|	LOOK|
|---|--|--|--|
|starts|	First request|	First request|	T=0|	First request
|Fills request in path|	No	|No|	Yes|	Yes|
|Changes side	|Yes|	Yes|	No|	No|


Example
```
Job Location Ready FCFS  SSTF  LOOK  SCAN
A    40       12    52    52   52     40
B    30       35    62    62   42    170   
C    36       50    68    56   96    164
D    60       51    92    92   72     60
E    62       74    94    94  122    138
F    94      125   157   157  157    294

if there is no job left, then FCFS,SSTF,LOOK will wait at that location
while SCAN goes on moving.
FCFS and SSTF first decides then move while LOOK and SCAN fills the request in path
LOOK changes direction if no job in that direction left but there is in another direction
```
```
Disk scheduling: Let locations 0..100 [Total 101]
Job  Arrival  Location  FCFS   SSTF   SCAN  LOOK  C-SCAN
A      0        45       45     45     45    45     45
B      42       40       50     50    160    50    140 
C      43       44       54     46     44    44     44  
D      60       80       96    100     80   100     80 

Job Arrival Location  LOOK
A     0      60        60
B    30      42        42
C    48      45        95
D    56      65        65
M    62      70        70
E    71      80        180
F    92      20        120
```
