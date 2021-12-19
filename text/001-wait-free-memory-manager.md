# Wait-free memory manager

- RFC PR: 
- Tracking Issue:
- Author: Luhuanbing 

## Summary

I present a new wait-free memory reclamation scheme, that is simultaneously addresses the challenges of high performance, high memory efficiency, and wait-freedom. Before that, i must explain the definition of the lock-free and wait-free.

> The both of two are used to define the concurrency algorithm, the method, which is access the shared object in the shared memory. The lock-free means that only if tasks can make progress, there is at least one task can move forward. The wait-free means only if the task is alive, then it can move forward. The difference of lock-free and wait-free is starvation. The most lock-free algorithms are based some competitive primitives. When many tasks in the race areas, maybe there is one lucky task always win, and other tasks can do nothing. Not turn that tasks in the job, just bad luck. That also named on “live lock”. The wait-free is stronger than lock-free, it guarantees any tasks can finish jobs in “limit steps”. It is not fittness that we use CAS operations in the loop, because some tasks may wait all the time.   

This design garantees complete wait-freedom even when threads are dynamically recycled, asynchronously recliams memory in the sense that any thread can reclaim memory retired by any other thread, and ensures balanced reclamation workload across all threads.

## Motivation

Trying to control the object lifetime from the allocation to the destory and reclaimtion in the stream lifetime. 

## Detailed design

This is the bulk of the RFC. Explain the design in enough detail that:

- It is reasonably clear how the feature would be implemented.
- Corner cases are dissected by example.
- How the feature is used.

## Drawbacks

Why should we not do this?

## Alternatives

- Why is this design the best in the space of possible designs?
- What other designs have been considered and what is the rationale for not
  choosing them?
- What is the impact of not doing this?

## Unresolved questions

What parts of the design are still to be determined?