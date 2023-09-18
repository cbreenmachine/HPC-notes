# Speed Baby Speed

## Preliminaries
- Wall clock time: includes housekeeping (assigning node, OS tasks)
    - Meaningful to user
    - Not always useful to improving speed
- CPU Execution time: time to execute *your* program. You're not penalized by context switches etc.
    - User time: time on processing instructions
    - System time: opening files, etc.
    - Did you write that function? Do you have control? Then it's user time. You're not going to make reading/writing faster etc.

## Thinking About Clock Cycles

Ideall, one instruction complete per clock cycle.

CPU Execution Time = Instruction Count \times CPI \times Clock Cycle Time

CPI: clock cycle per instruction

ILP can allow for less than one clock cycle per instruction

If memory is accessed in a disorganized way, you'll get many clock cycles per instruction.

## Static Random Access Memory: SRAM
- Element: saves the state of a bit (charge or no charge)
- To store one bit, you need six transistors. Four comprise the *flip-flop*, and two that access the flip-flop.
- Very short access time
- But because you need six transistors, its expensive (tranistor-wise)
- Access time is 4 to 5 cycles

## Dynamic Random Access Memory: DRAM
- Stored as a charge in a capacitor
- Very cheap
- Can leak, so needs refreshing (comes ar a small 0.1% overhead in memory access)
- Access time is 10s od cycles

Because of these tradeoffs, we usually get SRAM for cache memories, and DRAM for main memory.

Processors have gotten much faster relative to memory. The bottleneck has become SRAM/DRAM. Solution is memory hierarchy

## Memory Management Unit (MMU)
Fastest

L0 (registers) --> L1 and L2 (SRAM) --> L3 (SRAM) --> L4 (DRAM) is main memory --> etc.

Caches are physically on the chip, so its faster to move data around.

*(CPU-specific)*
Register files
L1 data cache + L1 instruction cache --> L2 unified cache

L3 unified cache is shared by all cores.

## How Big Should the Cache Be?
Optimization problem where you're trading off size (more is better), and access (shorter is better). Don't want to jump around too much, but if you 

## Locality
- Temporal locality: recently accessed location are used 