# User-Level Thread Library (C++)
This project implements a User-Level Thread (ULT) Library in C++ as part of an Operating Systems assignment. The library enables the creation, management, and scheduling of threads at the user level, bypassing the kernel’s native thread handling.

## Key Features:
..* Thread Management: Supports creating, terminating, blocking, and resuming threads. Each thread is assigned a unique ID, and the main thread (ID 0) is always present.
..* Round-Robin Scheduling: Implements the Round-Robin (RR) scheduling algorithm, where each thread is allocated a quantum of CPU time. The library preempts threads when their quantum expires, or if they block or terminate.
..* Virtual Timer: Uses the virtual timer (SIGVTALRM) to manage the quantum duration for each thread.
..* Thread States: Each thread can be in one of three states: READY, RUNNING, or BLOCKED, and transitions between states are managed by the library functions.
..* Sleep Functionality: Threads can sleep for a specified number of quantums before being re-queued into the READY state.
..* Error Handling: Provides clear error messages when system calls or thread operations fail, ensuring robust operation.

## Library API:
The public API of the library is exposed through the uthreads.h header file. It includes the following main functions:
uthread_init(int quantum_usecs): Initializes the thread library and sets the quantum time.
uthread_spawn(thread_entry_point entry_point): Spawns a new thread.
uthread_terminate(int tid): Terminates a thread.
uthread_block(int tid): Blocks a thread.
uthread_resume(int tid): Resumes a blocked thread.
uthread_sleep(int num_quantums): Puts the currently running thread to sleep for a specified number of quantums.
uthread_get_tid(): Returns the ID of the currently running thread.
uthread_get_total_quantums(): Returns the total number of quantums that have elapsed since the library was initialized.
## Usage:
The library can be linked to user programs to provide user-level thread management and scheduling.
The static library is compiled using a provided Makefile and can be linked with other programs by including uthreads.h.
How to Run:
Clone the repository, compile the project with make, and link the generated static library (libuthreads.a) with your own programs.
Refer to the examples in the repository for usage and API documentation.
