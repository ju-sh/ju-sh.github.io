# Workshop on ARM based HPC: Day 1

 - Speaker: Phil Ridley
 - NSM (National Supercomputing Mission) Industry Talks
 - NSM Nodal Centres for Training in HPC and AI
 - [Info link](https://www.cse.iitm.ac.in/~rupesh/events/arm2021/)
 - Date: 02-Mar-2021

---

# ARM
 - Advanced RISC Machines


 - ARMv8 is the current version. Came out in 2011.


 - Scalable vector
 - Vector register

 - ARM makes only the design and does no chip manufacture.

 - ARM neoverse

## Fugaku
 - Biggest ARM based deployment
 - Japanese supercomputer
 - Uses RISC (ARM Architecture license)
 - Currently the most powerful supercomputer
 - 512 bit vector registers
 - Delivered early to assist with Covid crisis

# ARM licenses
 - Core license
 - Architecture license

## Architecture license
 - Just a recipe
 - More freedom (in design?)
 - Targeted
 - Architecuture validation done to ensure compatibility??

# More stuff
 - European Processor Initiative (EPI)
 - Ampere Altera (processor): 80 cores?? per socket??
 - SKU (Stock Keeping Unit)
 - Amazon Annupurna processors
 - NEON vectorization
 - SVE vectorization (Scalable Vectorization Extension)
 - Intel skylake
 - 4-way SMT (Simultaneous Multi-Threading)
 - CMOS FinFET
 - 128 Neon
 - 64KB L1$ per core
 - PCIe
 - CMG
 - Cache sharing
 - Memory bandwidth
 - u-arch
 - NUMA node
 - EBS bandwidth
 - Single socket processor
 - ARM Neoverse N1
 - PFLOP Rmax, Rpeak
 - Mont Blanc
 - DDR3,DDR4 SDRAM (Double Data Rate Synchronous Dynamic RAM)
 - Blades
 - EDR
 - Cray Linux
 - Infiniband
 - Isambard (a computer)
 - High speed Aries interconnect
 - EuroHPC (organization)
 - ODM (Original Design Manufacturer)
 - OEM (Original Equipment Manufacturer)
 - OpenHPC (https://developer.arm.com/solutions/hpc/hpc-software/openhpc)
 - Linaro (company)
 - Aarch64: aka ARM64. 64bit extension of ARM
 - Ceph file system (distributed storage system??)
 - CapEx
 - OpenBLAS (Library) (Basic Linear Algebra Subprograms)
 - FFTW (Library) (Fast Fourier Transforms in the West)
 - OpenMP
 - MPI (Message Passing Interface)
 - wiki.arm-hpc.org
 - HPC benchmarks
 - Mailing list: arm-hpc.groups.io/g/ahug
 - SVE ACLE types
 - ARM is developing SVE2
 - ARM DDT for scalable debugging. Based on GDB.
 - ARM MAP for parallel profiling
 - Auto-vectorization for SVE and NEON
 - flang f18 project (now part of LLVM) written in C++
 - low level math routines: BLAS,FFT,LAPACK
 - NAG's test suite
 - System on Chip
 - Transcendentals (libm)
 - Sparse matrix operations: SpMV and SpMM (MM => Matrix multiplication?)
 - DGEMM performance
 - https://icl.cs.utk.edu/papi/
