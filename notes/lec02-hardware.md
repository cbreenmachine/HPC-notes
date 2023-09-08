# Hardware

## High-Level Ideas

*Instructions* involve doing something
*Data* involves moving something 

Instructions run fast, but data movement requires more thought.

## From C to Machine

1. C code is starting point
2. Intermediate representation is what compiler produces. This can be optimized (?)
    - Comments stripped out
    - Spaces stripped out
3. Assembly code maps one-to-one against machine code
4. Machine code is what the control unit "digests"

See [godbolt](godbolt.org) shows you how C code can be compiled into completely different machine instructions.

## "Storage"
Both instructions and data are stored as 0s & 1s. Instructions are often 32 or 64 bits (you cannot control). Data--you do have control over--and it is stored in 8, 16, 32 bits.

### von Neuman MOdel (Princeton Model)
The processor aka chip includes two units. The control unit (CU) keeps the instructions, and the arithmetic logic unit (ALU) keeps the data. There is information flow between these.

Data is brought over from cache. 

Instruction control
1. Memory address is passed to the instruction cache, and instructions are outputted

#### Control Unit
- CU controls the *datapath:* functional units, etc.
- Instruction set architecture (ISA) takes a couple hundred keywords like `move`, `push`, `pop` which are the simplest building blocks
    - CISC
        - Complex but expressive
        - Variable length 
        - Intel is chief proponent, also AMD
    - RISC
        - Simple, fast, constant length (32 bit) instructions
        - NVIDIA, Samsung, Qualcomm
        - Good on embedded devices


#### Arithmetic logic unit
Can add, subtract, and also has special functions like sin(), exp()

## Fetch-Decode-Execute (FDX) Cycle
- Keeps CU and ALU busy
- Done on each instruction until no more instructions

**Fetch**


## MIPS ISA
Type I: (I)mmediate
    - 6 bits for opcode (basic operation)
    - 5 bits for register stored (rs)
    - 5 bits for register target (rt)

Type R: 
    - Similar allocation
    - Need rd for register destination
    - shamt field (shift amount)
    - funct field

Type J: (J)ump
    - What does this mean??

## Chip Microarchitecture
ISA defines a vocabulary
Microarch. refers to how the silicon is organized to implement ISA. E.g. how many tranistors go into "implementing" IDA standards

## Transistors
A humble thing. 

- 1 transistor gets you the `NOT` operation
- 2 transistors get you `OR`
- 2 transistors can also get you `AND`

From this you can build up more complicated things...


## Clockcycle

Takes many clockcycles/ticks to wrap up. Moore's law refers to the number of transistors per unit area. Down to 4nm feature size (close to quantum limit?)

## Innovation and Improvement
The price of Gflop/second

- 186 billion dollats in 1961
- 1 cent in May '23

## Questions
What's difference between register and memory address?



