# Processes, threads and resources

## Context

In a concurrent system there may be multiple processes running concurrently. We want to develop a UML of the system, according to the following requirements:

* Each process is composed of one or more threads. Both processes and threads can access shared resources, which can be of two types: global, which are owned by the system and can be shared by any thread of any process, and local, which are owned by a particular process and can only be shared by threads of that process.

* The system is limited by the number of processes, threads and resources it can manage: The maximum number of processes is the system is 128, and each process can have a maximum of 32 threads. However, the total number of threads in the system can never exceed 64, and the total number of resources (sum of local and global) cannot exceed 128.

* If a thread of an active process wants to acquire a shared resource that is free, it acquires it directly. The acquisition implies that the shared resource becomes occupied and that its owner at that moment is the thread that has acquired it. However, if a thread tries to acquire a resource that is being used by another thread, the requesting thread is blocked waiting for its turn. Each resource maintains a queue of waiting threads, so that if a thread requests an occupied resource the thread is inserted into the queue. A thread can use several resources at the same time, but if it is blocked when trying to acquire one it cannot request others and therefore can only be blocked by one resource at most.

* The thread that owns the shared resource can release it when it has finished using it. When a thread releases a resource, the first of the threads in the queue for that resource gets to use it. In case the queue is empty the resource will be unoccupied.

* Processes can be in three different states: running, sleeping or available. In the system there is always only one process running and the rest are asleep or available. None of the threads of the running process or the available processes can be locked on a global resource. On the other hand, all sleeping processes must have some thread locked on some resource.

## Questions

1. Develop a UML class diagram with the elements described above and the relationships between them.

2. Specify in OCL all the restrictions and integrity constraints described above.

3. Include in the class model the necessary operations to specify the actions of "acquiring" and "releasing" a resource by a thread, as well as their pre- and postconditions. 











