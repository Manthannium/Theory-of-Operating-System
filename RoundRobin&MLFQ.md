# Round Robin
```
There is fixed quantum k say. We maintain queue.
Each process runs for k or less (if completes) according to queue.
New processes are inserted at the end of queue.
If there is no process in queue then current process is re-executed for k quantum
```
Examples
```

```

# Multilevel feedback queue (MLFQ)
```
It is extension of RR. here also quantums are there and process exectues cyclically
Here we have two queues - Low and High priority
High priority queue has smaller quantum than Low priority queue
New processes are send to HPQ and once pre-empted then send to LPQ

When new process comes in, then running process (if from LPQ) then its preempted
even though the quantum is not completed
```
