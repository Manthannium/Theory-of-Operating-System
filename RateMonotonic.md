# Rate Monotonic Scheduling
```
priority is given to most frequent job rather than shortest job
But however take care of deadlines of all jobs
If one misses deadline then it is infeasible
Also check for % CPU use before solving
```
```
1. Time periods of Job A and B are 20 and 30 respectively. Their service times are 8 and 16 respectively.
In a span of 60 A0, A1 and A2 will arrive at time t=0, 20 and 40 respectively. Their deadlines are 20, 40 and 60 respectively.
In a span of 60 B0 and B1 arrive at t=0,30 with deadline 30,60 respectively.
A0:0-8 B0:8-24 A1:24-32 B1:32-48 A2:48-56

2: Time periods of Job A and B are 20 and 30 respectively. Their service times are 14 and 12 respectively.
It is infeasible because job A is taking 14/20=70% of cpu time. B is taking 12/30=40%. 70+40>100.

3: Time periods of Job A and B are 20 and 50 respectively. Their service times are 3 and 35 respectively.
3/20+35/50=15%+70%<100 is feasible but can not be done.
A0:0-3 B0:3-38 A1:38-41  A1 misses deadline of 40.

4: Time periods of Jobs A, B and C are 40, 70 and 190 respectively. Their service times are 10, 5 and 40 respectively.
A0:0-10 B0:10-15 C0:15-55 A1:55-65 B1:70-75 A2:80-90 A3:120-130 B2:140-145 A4:160-170 C1:190-230
A5 arrived at t=200. B3 at t=210. At t=230 two jobs with service time 10,5 and deadline 240,280 are available.

Which job should be given preference. B is shorter but time period of A is less hence A5 is done.
It is rate-monotonic scheduling. 
The Rate Monotonic scheduling algorithm assigns priorities to different tasks according to their time period. 
That is task with smallest time period will have highest priority.

5: Time periods of Job A and B are 30 and 70 respectively. Their service times are 10 and 35 respectively.
A0..A6 have ready time 0,30,60,90,120,150,180 and deadline 30,60,90,120,150,180,210 respectively.
B0..B2 have ready time 0,70,140 and deadline 70,140,210 respectively.
A0:0-10 B0:10-45 A1:45-55 A2:60-70 B1:70-105 A3:105-115 A4:120-130 B2:140-175 A5:175-185 misses deadline.
A0:0-10 B0:10-45 A1:45-55 A2:60-70 B1:70-105 A3:105-115 A4:120-130 A5:150-160 B2:160-195 A6:195-205.
Here B2 is not allocated cpu at t=140 because a higher priority job will arrive at 150.
Why at t=70 B1 was not made to wait?
A0:0-10 B0:10-45 A1:45-55 A2:60-70 A3:90-100 B1:100-135 A4:135-145 A5:150-160 B2:160-195 A6:195-205 is also possible.

Conclusion: A job is not allocated cpu if a higher priority job is likely to come during its processing. 

6: Time periods of Job A and B are 40 and 70 respectively. Their service times are 10 and 45 respectively.
A0..A6 have ready time 0,40,80,120,160,200,240 and deadline 40,80,120,160,200,240,280 respectively.
B0..B3 have ready time 0,70,140,210 and deadline 70,140,210,280 respectively.
A0:0-10 B0:10-55 A1:55-65 B1:70-115 A2:115-125 misses deadline.
Let us make B to wait at 70.
A0:0-10 B0:10-55 A1:55-65 A2:80-90 B1:90-135 A3:135-145 B2:145-180 A4:180-190 A5:200-210 B3:210-245 A6:245-255
Let us make B to wait at 145
A0:0-10 B0:10-55 A1:55-65 A2:80-90 B1:90-135 A3:135-145 A4:160-170 B2:170-215 misses deadline.

Conclusion: Whether a job is made to wait or not allocated has no fixed rule.

```
