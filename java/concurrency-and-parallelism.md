# Concurrency and parallelism

### Critical section and syncronization

- Critical section is a limited resource required for task execution. It's critical because the process can't go further without passing it, so the worker must get access to this resource to accomplish the task.
- Managing access to the critical section for concurrent tasks is called synchronization because it's blocking and consecutive or, in other words, synchronous.

### Concurrency

**Concurrency** is an ability to execute different tasks simultaneously in overlapping periods and no predefined
 order in an environment with some scarce shared resources required for task execution.

Concurrency appears when there is a scarce shared resource (critical section), and workers compete for access to it. For concurrency, it's necessary to have:

- more than one task in operation
- at least one critical section for these tasks

There is no such thing as concurrency for one task, it takes two to tango, so the second name of concurrency is multitasking.

### Parallelism

Parallelism is an ability to process tasks simultaneously by different executors. These can be either several independent tasks or one big task split into smaller subtasks and divided between workers.

The presence of multiple executors is an essential condition for parallelism. There are many executors processing tasks in parallel, so the second name of parallelism is multiprocessing.

## Conclusion

- Concurrency is about dealing with multiple tasks at once in the environment with shared resources.
- Parallelism is about processing a lot of work by several executors in parallel.
- Concurrency and parallelism often intersect and appear together. They can mutate one to another.
- Practically, all combinations of concurrency and parallelism are possible.