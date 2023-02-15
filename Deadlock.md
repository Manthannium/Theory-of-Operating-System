# Deadlock
```
When jobs wait for resources but can't get them as resource allocation graph makes cycle
```
```
Job C:[run 10][needP][run7][needQ][run 3]
Job D:[run 5][needQ][run8][needP][run 4]
Job E:[run 12][needP][run 1]

Normal execution is following
C:[0-10][10-17P] waits for Q and holds P
D:[0-5][5-13Q] waits for P and holds Q

Deadlock occurs!
```
### Deadlock Prevention (Static method)
```
Do not demand a lower resource when hold higher
```
```
P is lower Q is higher resource.
Job C:[run 10][needP][run7][needQ][run 3]
Job D:[run 5][needPQ][run8][run 4]
Job E:[run 12][needP][run 1]

C:[0-10][18-25P][25-28Q]
D:[0-5][5-17PQ]
E:[0-12][17-18P] 

At t=17 P can also be given to C also

Job C:[run 10][needP][run7][needQ][run 3]
Job D:[run 5][needPQ][run8][run 4]
Job E:[run 12][needP][run 10]

C:[0-10][10-17wait forP][17-24][24-27PQ]
D:[0-5][5-17PQ]
E:[0-12][12-27wait for P][27-37P]

At t=17 P can also be allocated to E( in place of C)
```
### Deadlock Avoidance (dynamic method)
```
At every stage we try not to come in danger situation
So we may not give resource to job even if it is availavle to avoid deadlock
```
```
Job C:[0-10][17-24P][24-27PQ]
Job D:[0-5][5-13Q][13-17PQ]
Job E:[0-12][12-13P]

Even though C needs P at t=10 and is available but we will not give
at t=12 if E asks we will give then at t=13 we give to D but not C
injustice is imparted to C but this will avoid deadlock
```
