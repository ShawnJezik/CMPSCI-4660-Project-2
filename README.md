# CMPSCI-4760-Project-2

Shawn Jezik
10/1/2022

**The Purpose**
The goal of this homework is to become familiar with concurrent processing in Linux using shared memory. You
will use multiple concurrent processes to write into a file at random times, solving the concurrency issues using the
multiple concurrent processes algorithm (algorithm 4 in my notes) to synchronize processes. Your job is to create
the environment such that two processes cannot write into the file simultaneously and yet, every process gets its turn
to write into the file.

**Implementation**
You will be required to create the specified number of separate slave processes from your master. That is, the
master will just spawn the child processes and wait for them to finish. The master process also sets a timer at the
start of computation to specified number of seconds. If computation has not finished by this time, the master kills
all the slave processes and then exits. Make sure that you print appropriate message(s).
master will also allocate shared memory for synchronization purposes. It will open and close a logfile but will not
open cstest. cstest will be opened by the child process as it enters critical section (before the sleep) and closed
as it exits.
In addition, master should also print a message when an interrupt signal (^C) is received. The child processes
just ignore the interrupt signals (no messages on screen). Make sure that the processes handle multiple interrupts
correctly. As a precaution, add this feature only after your program is well debugged.
The code for master and slave processes should be compiled separately and the executables be called master and
slave.
Other points to remember: You are required to use fork, exec (or one of its variants), wait, and exit to manage
multiple processes. Use shmctl suite of calls for shared memory allocation. Make sure that you never have more
than 20 processes in the system at any time, even if I specify a larger number in the command line (issue a warning
