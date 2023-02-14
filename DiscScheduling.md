# Disc Scheduling
```
There is single server that can move from location 0 to 100
Jobs (Serve requests) arrives at specific location
It takes 0 time in serving and 1 unit of time in traversing 1 unit on disc
All the schedulings are non-pre-emptive. 
Assuming we have locations from L=0 to 100 and at t=0 out pointer/server is at L=0 
```
### FCFS (First Come First Serve)
```
Pointer starts to move from L=0 when it sees first request
Serves the request according to their ready time. 

Advantage – naturally serve those who comes first
Disadvantage – more direction flips and path repetitions 
```
### SSTF (Shortst Seek Time First)
```
Pointer starts to move from L=0 when it sees first request
Serves the request according to proximity. Request whose location is nearest to the pointer is served first. However, it first makes the decision and then moves. So even if some request come in the path but was not decided earlier then it won’t execute that.

Advantage – why should we seek much time in travelling? Lets do task that requires less travelling time. Useful in trip. When you go to some place, you try to visit nearby places. 
Disadvantage – more direction flips due to greediness of nearer location

```

Example
```
Job Location Ready FCFS  SSTF  LOOK  SCAN
A    40       12    52    52   52     40
B    30       35    62    62   42    170   
C    36       50    68    56   96    164
D    60       51    92    92   72     60
E    62       74    94    94  122    138
F    94      125   126   126  154    294
```
