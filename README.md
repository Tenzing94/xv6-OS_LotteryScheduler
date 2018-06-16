# xv6 "Implementing a Lottery Scheduler"

### Assignment
For this assignment, you will implement and test _lottery scheduling_ , a randomized algorithm
(discussed in class and in the reading) that allows processes to receive a proportional share of the
CPU without explicitly tracking how long each process has been run.
Specifically, you should modify xv6 so that:
1. Each _struct proc_ has an additional field, _tickets_ , that tracks how many tickets it
has.
2. New processes are assigned 10 lottery tickets when they are created.
3. When the scheduler runs, it picks a random number between 0 and the total number of
tickets. It then uses the algorithm described in class to loop over runnable processes and
pick the one with the winning ticket.
4. User processes have a new system call, _settickets_ , that allows a process to specify
how many lottery tickets it wants. Normally this would be a bad idea, since it would let a
process hog the CPU by specifying an arbitrary number of tickets -- but xv6 has no
security anyway, so this is not that big a deal.
