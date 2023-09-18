# Registers

## (Refresher) Fetch-Decode-Execute (Write)
Operates on instructions
But instructions need to be stored somewhere (Princeton model does not distinguish between instructions and data). Either way, the data (w/ or w/o instructions) needs to be stored *somewhere*.

## What is a Register?
- Hardware asset that stores information, be it data value or instruction
- Storage type with shortest latency
- Part of CU and ALU combo
- Size and \# of bits is specific to an ISA
- Size of one register is 32 bits (now 64 bits)

### Types
- Current instruction register (CIR)
- Program Counter (PC): stores *address* of instruction
- Memory Data Register: data going into or out of ALU, waiting to be stored in memory
- Memory Address Register (MAR): stores *address* of instructions

Stack pointer, global pointer, and frame pointer

Subroutine arguments, temporary variables, saved temporary variables

### Why Can't we Have More Registers?
- Need to change the design of chip
- Change the nature of instructions (so ISA gets impacted)

**Everything** gets piped through a register at some point

# Pipelining

Use an assembly line model. You have many employees, and there's no need to have more waiting than neccessary.

## High Level Idea
Output of process 1 is the input of process 2
Function run happens once every clock cycle 
- Typically clock cycle ix 1 billion pulses / sec
- Limited by physics (melts if you crank this up too much)

## FDX(W) Cycle Revised
*In reality, pipelines are more like 10-15 (sub)-stages; many of these stages involve error handling, storing, loading, passing to next process, etc.*

1. Fetch
2. Decode
3. Execute
4. Write

### Clicks per Stage
For example
- 4 clock cycles (ticks) for storing
- 5 ticks for loading
- 4 cycles to add

## Idealized Pipelining
Want each stage to take the same amount of time (called **balanced**)

- **Benefit 1:** If you have *p* stages, you can get almost *p* times faster (ignoring the bias in the beginning)
- **Benefit 2:** No code rewrite--very easy (effortless) for us using the machine. Handled automatically by computer

## Pipelining Hazards

**Structural Hazards:** when multiple hardware assets want the same instruction?
- Instruction in stage 5 and 9 both need the same special register to store a variable
    1. Register could be commandeered
    2. Could introduce a bubble in the pipeleine, where both instructions have access sequentially
    3. Out-of-order execution (OOOE) done statically (at compile time) or dynamically (at run time)

**Data Hazards:** when you want access to the same data for multiple instructions, so you need to break the "retiring" that's usually done at the end of the FDX cycle

**Multipl-Issue:**
More than one instruction is processed by the same core in teh same clock cycle. A chip that can handle his is called a **superscalar**

*Static multiple-issue*
- Uncommon (some intel)
- Predefined

*Dynamic*
- Determined at run time, dedicated hardware resources that identify and execute additional work
- Intel, AMD, IBM, NVIDIAs
- Fetch-decode-(Holding buffer)-execute, where multiply FDs happening at the same time

## Instruction-Level Parallelism (ILP)
- Instructions belong to the same program or process (one thread)
- Bag of tricks
    - Out-of-order
    - Register renaming
    - Speculative execution
    - Others

## Thread Level Prallelism (TLP)
- Happens on a single core 
- Difference processes or different threads executing simultaneously 
- Happening on one hardware core!

## Compare and Contrast
ILP is associated with one process counter. Multi-threading needs at least two process counters. A thread shares the same (virtual) memory space. So if you're running MATLAB and Spotify, you'd have one 

Each thread gets its own ...

## HTT
HTT is helpful when running completely different processes (e.g. MS word and Spotify), but not helpful with HPC

TLP induces security issues?

1. Coarse multi-threading (old school)
2. Simultaneous multi-threading
