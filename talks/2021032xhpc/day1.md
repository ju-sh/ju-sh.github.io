# HPC workshop - Day 1

 - Speaker: Nikhil Hegde from IIT Dharwad
 - Date: 20-Mar-2021
 - [Info link](https://www.cse.iitm.ac.in/~rupesh/events/hpc2021/)
 - NSM HPC 2-day workshop

Couldn't actively participate in the lab session (didn't have access to a cluster to try it out).

Chandra: An HPC cluster at IITPKD.

The giant computers consists of many smaller computes linked together.

# Basic terminology

## FLOPS
 - Floating-point operations per second.
 - aka flop/s

## Node
Standalone computer in the HPC cluster.

## Master / login node
The one with which the user interacts directly.

## CPU/Processor and sockets
Socket: Some vendors term multicore CPU sockets.

## Virtual CPU
A VM assigned to a single CPU core.

## Interconnect
 - **Cabling** and associated devices to connect the different components of the HPC cluster together.
 - Cabling determines the **topology**.

## Storage
###$HOME
Where you land upon logging in

### $SCRATCH
 - not just an env var
 - a faster memory where we keep all data needed for executing the task
 - Eg: Lustre, BeeGFS

### /tmp (optional)
Storage may be available in individual nodes as well.

### Storage servers
Dedicated for storage

## Batch system
 - Consists of a job scheduler and resource manager.
 - Provides user interface to submit, run and monitor jobs

### Slurm
 - Slurm workload manager.
 - Formerly stood for Simple Linux Utility for Resource Management

### PBS
 - Portable Batch System
 - A job scheduler like SLURM. ie, a batch system.

### Platform LSF
Platform Load Sharing Facility

## Paritions/queues
 - Logical grouping of some nodes in the cluster.
 - Single node can theoretically belong to multiple partitions but this is not usually practiced.
 - Defines attributes and limits for a job submitted to this partition.

## Software
ICC, MPICH, NVProf, Intel Parallel Studio, etc.

## Cluster
Consists of
 - Master node (front-end)
 - Back-end
 - Interconnect
 - File system ($HOME, $SCRATCH, etc)


Log in at Master node (possibly using SSH).

# Linux commands
scp : to copy files between a remote server and your computer.

# Life of a job
## Job creation
 - Max num of nodes,cores needed
 - Max amount of mem, time needed
 - Commands involved

## Job submission
Means,
 - No syntax errors
 - Amount of requested resources can possibly be allocated.
 - Job object created in the queue in which it is to executed.
 - Whether exclusive access to the core is needed.
 - A job id is returned.

## Job execution
 - Requested resources becomes available.
 - From here on, you can't request more resources.
 - Commands specified are executed one by one.

## Job monitoring
 - Can delete the job if needed.
 - Check job status.

## Job completion
 - Normal or abnormal completion
 - May also be because the job exceeded its stated resource/time requirement.

# Programming clusters
All about taking advantage of the parallelism.

## Process
 - Self contained.
 - Has its own share of resources allocated to it.
 - An illusion that it owns an entire computer for itself

## Threads
 - Belongs to a process
 - Shares resources with other threads of the process.
 - An illusion that it owns an entire processor core for itself?

## Kinds of execution
### Sequential program
### Concurrent program
#### Multiprogramming
Threads muxing their execution on a single processor.
#### Multiprocessing
Threads muxing their execution on multiple cores.
#### Distributed computing
Threads muxing their execution on multiple nodes.

## Parallel program
Program designed to execute on hardware supporting parallelism.

## Flynn's taxonomy
 - Categories of computing systems
 - Based on how processors see instructions and data.

### SISD (Single Instruction Single Data)
Single core computer + single stream of data

### SIMD (Single Instruction Multiple Data)
 - Parallel hardware
 - Same instruction but multiple 'slices' of data are processed at the same time.
 - All cores execute the same instruction in the same clock cycle but operate on different data.
 - Eg: GPUs, modern CPUs with SIMD components.

### MISD (Multiple Instruction Single Data)
Not that common? Not sure...

### MIMD (Multiple Instruction Multiple Data)
 - Clusters belong in the MIMD category.
 - Most common type of parallel computer
 - Cores may be operating in sync or async
 - Eg: clusters, supercomputers, multi-core CPUs.

 - Clusters are specialized supercomputers?
 - Clusters => different nodes may be having different OS.

## Parallel hardware
Categorization based on hardware
 - Shared memory architecture: all processors share the same mem
 - Distributed memory arch: each processor has some mem allocated to it. (but are these mem or processor that are connected??)

## Data parallelism
Threads execute the same function but operate on different data.

## Control/task parallelism
Like carpenter getting the window ready when the mason is building the wall.

## OpenMP
 - For shared memory programming.
 - C/C++/Fortran
 - Single Program Multiple Data (SPMD)
 - Seamless automatic scaling: Can add more processors without having to modify the programs. This wasn't possible with pthreads??
 - Scalable, portable alternative to data-parallel computing on shared memory architectures.

## Programming in OpenMP

    // executes as many threads as there are processors (possible to change this number)
    #pragma omp parallel 
    // Divides a for loop
    #pragma omp for 

Like (not sure if correct),

    #pragma omp parallel 
    {
        int sum = 0;
        #pragma omp for 
        for(int i=0; i<100; ++i)
        {
            sum += i;
        }
    }


 - Programmer still responsible for handling data races.
 - Execution begins with a **master thread**.
 - Master thread spawns worker threads.
 - Worker threads 'joins' master thread (after execution?)

    omp_set_num_threads(P)  // set number of threads

## Non-determinism
The exact order of instructions executed is not deterministic (not a total ordering, but a parital ordering?).

### Example: Sum of an int array

    sum = 0  // set by master
    
sum is shared among workers. Only worker should set it at a time => possible **data race**.

Alternatively, make two variables `sum1` and `sum2` so that two independent courses of action can proceed.

Master joins the result (the partial results computed by the worker threads) at the end.


## Distributed memory programming
 - Program executes as a collection of processes.
 - Each process/processor has its own memory.
 - Total memory available = sum of that of all processes.
 - Data exchange between processes => processes need to cooperate. ie, explicit communication.
 - Every data element belongs to the memory of one of these processes.
 - If a data element is placed in the memory of a process which barely uses it may mean avoidable communication overhead. => more complex than a shared memory architecture.
 - Most programs are written in SPMD model.
 - Computing power and cost scaling better than shared memory. (because of stuff like rack-mounted blades?)


## An example C program using MPI

    #include<mpi.h>

    int main(int argc, char *argv[]) {
        // Initialize MPI env
        MPI_Init(&argc, &argv);

        // rest of the code

        // Release system resources
        MPI_Finalize();
    }

We got to divide the work first.

We can use the values of rank and size for this.


### Ranks in MPI
 - Ranges between 0 to 5. ie, ∈ [0,5]
 - Like a process number?

### Size in MPI
Number of processes in the execution environment?

## A very rough depiction of some MPI commands

    MPI_Send(send_buffer, count of sent items, data type of sent items, dest process id, message id)
    MPI_Receive(receive buffer, count of received items, any message id (for source??), from any process id, )

    // Aggregate results
    MPI_Gather(send_buffer, count, datatype, receive_buffer (from master?), receive_count, receive_type, ...)

# Git repo
[https://github.com/IITdhtraining/hpc101](https://github.com/IITdhtraining/hpc101)

# MPI and OpenMP difference
 - MPI for shared memory architecture
 - OpenMP for distributed memory architecture (distributed computing)
 - Hybrid systems possible. ie, same system could use both MPI and OpenMP.

# Interesting
 - `mpic++ prog.cpp`
 - `mpirun -n10 helloworld  # Create 10 copies of this project`
 - valgrind and cachegrind
 - gprof
 - opanacc
 - openmp
