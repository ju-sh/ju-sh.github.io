# Workshop on ARM based HPC: Day 2

 - Speaker: Phil Ridley
 - NSM (National Supercomputing Mission) Industry Talks
 - NSM Nodal Centres for Training in HPC and AI
 - [Info link](https://www.cse.iitm.ac.in/~rupesh/events/arm2021/)
 - Date: 03-Mar-2021

---

 - W register: 32 bits (lower half of X)
 - X register: 64 bits
 - D register: 64 bits (lower 64b of Q)
 - Q register: 128bits (lower half??)
 - word size : 128 bits?

## Neon intrinsics
 - ACLE: ARM C Language Extensions
 - `#include arm_neon.h`
 - ARM Neon doesn't have SVE. Only 128b registers.
 - Advanced SIMD

## Scalable Vector Implementation
 - Vector length: hardware implementation choice from 128b to 2048b.
 - Hardware sets VL.
 - Software => vectors have no length.
 - Same binary code runs on hardware with different VL.    

### Vector length agnostic
 - There are programming models that allow software to scale to available vector length.
 - No need of new ISA or rewrite or recompile for new vector lengths.

### Auto-vectorization
 - Gather-load and scatter-store => Loads a single register from multiple scattered locations.

# SVE vs traditional ISA
 - SVE is a predicate-centric architecture

## Per lane predication
 - Operations are done in individual lanes each under the control of a predicate register.

## Example
 - Consider an example with 10 chunks of 4B (ie, 32b each)

### Aarch64 (Scalar)
 - 10 iterations over a 4B register
### Neon (128b Vector engine)
 - Two iterations over a 128b register (main loop) + two iterations of a drain loop over a 4B register
### SVE (128b VLA vector engine)
 - VLA => Vector Length Agnostic
 - Three iterations over a 16B VLA register with an adjustable predicate.
 - VLA -> portability, scalability improved


## SVE registers
### Scalable vector registers
 - Z0 to Z31 (Extends V0 to V31 of the NEON architecture)
 - Packed registers: DP,SP,HP

### Scalable predicate registers
 - P0-P7 (Predicates for load/store/arithmetic)
 - P8-P15 (Predicates for loop management)
 - FFR (First Fault Register for software speculation)

# VL (Vector Length)
 - Set by the CPU architect.
 - Any multiple of 128b upto 2048b
 - VL can be dynamically adjusted.
 - Implementation dependent
 - Can be reduced by OS/hypervisor


 - Predicates are not bit masks.
 - Predicate gives a lot of advantage that the compiler can use.


 - Lanes
 - LBB in assembly
 - Main loop
 - Drain loop: do anything that remains, if any.
 - auto vectorization
 - AVX in vector implementation
 - Disadvantages of a load/store architecture
 - software speculation
 - Full predicate
 - Partial predicate
 - A64 conditional instructions
 - Hotchips (conference)
 - Predicate instructions
 - Why double precison for double data type (general NQ)

# AI/ML With ARM
 - gvisor: Container sandbox by Google

 - Edge computing
 - ad hoc network
