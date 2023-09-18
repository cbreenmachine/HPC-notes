

## Review
WRT caches, remeber the principle of locality. Good locality can speed up code 30x, but in practice gains are smaller.

## Cacheing

*Write-hit*
Write-through: write immediately to main memory as well
Write-back: defer write to memory until replacement of line

*Write-miss*
Write-back + write-allocate is most common strategy

You have no control over caching, but you can choose to not violate locality.

## Tips for Obeying Locality
Focus on the inner loops of the "heavy" functions. This is where your costs really stack up.

**Temporal locality:** repeated reference to same variables are good
**Spatial locality:** "stride of one" reference patterns are good

*Where is this data that I'm referencing here coming from?*

# Memory Mountain Experiment

Measures effective bandwidth as a function of spatial and temporal locality.

**Effective bandwidth:** number of *useful* bytes read from main memory per second (MB/s). Nominal bandwidth is more hypothetical, best-case scenario.

**`volatile` keyword in C++** is used to not optimize away the value of a variable. I cannot think of a case where you'd use it in a way other than the way it's used on slide 13 of lecture 6.

**Prefetching:** controller sees a pattern in how you use data and it starts to anticipate, brings you data 

# Virutal Memory

In a waym the main memory (RAM) is the cache for the secondary storage. How do you evict "frames" of main memory? In cache land, you "evict" lines or blocks.

You can ask for an array of 1GB on a machine with only 512 MB of main memory. How?

**Memory lane:** tons of houses lined up, each contains 8 bits (a byte). How do you make sure you're not overwriting by running multiple programs? Or running the same program multiple times?

You have no control of the addressing process (the physical memory). There are already residents that inhabit the physical memory house. When you compile, the compiler assumes you have access to whatever you asked for, the virtual world, the pristine memory world. 

**Virtual memory:** a dally and quaint fictitous place

**Memory Management Unit (MMU)** manages the virtual memory.

**Page table** maps the page in virtual memory to a place in the physical memory.
