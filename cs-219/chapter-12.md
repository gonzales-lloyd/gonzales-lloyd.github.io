We now move to the connection between the CPU and external memory.  

The processor accesses memory and peripherals using an address and data bus.  The CPU-memory interface is one of the key bottlenecks limiting computer performance.  

When a processor is designed into a computer, the address space is divided into a memory map, where certain CPU address ranges are mapped to specific things.  

![[Attachments/Pasted image 20220413170613.png]]

Typically, RAM comprises most of the memory map. Ideally, we want RAM to be big, fast, and cheap, but we only get two.  For example, registers have extremely small latency, but have very small capacity and cost (literally) millions of dollars per gigabyte.  

Or, you can have tertiary memory, which has extraordinarily slow read rates, but has TBs of storage and costs practically nothing.  

# Caching

Memory systems tend to emulate the "big and fast" memory by using a cache, which is a smaller part of memory with fast local copies of small blocks of data from the larger, slower memory.  
![[Attachments/Pasted image 20220413171117.png]]

Caches store frequently-used data for faster access; for example, you know that a grocery store has a lot of things, but you only really need to take a few things from the grocery store.  And since you know what you want to eat for the next few days, rather than go to the grocery store everyday for the same thing, you just buy those things from the grocery store instead.  

A similar analogy is the desktop, drawer, and file cabinet analogy.  The desk is the register file, which is stuff someone's working with right now.  The drawer is something that's very close by and has more capacity, but takes a little more time to access than the desk.  And finally, the cabinet is the main memory, which is very big but relatively slow.

To get a data word from memory, the CPU requests it from the cache.  If the cache contains the word (the specific addressed memory), it gives it to the CPU, called a hit.  The percentage of requests that hit is known as the hit rate.  

If the cache does not contain the requested word, it stalls the CPU, loads the word from the main memory into the cache, and returns it to the CPU.  This is a miss, and the percentage of requests that result in a miss is the miss rate.  

Note how, unlike our one-cycle CPU model, the CPU does not have a direct connection to main memory; all of the memory requests are made to the cache.  The CPU itself doesn't know when a memory request results in a hit or miss, though it will eventually get the data it requests.  

## Locality
Caching works because of locality of reference.  There are two types of locality:
- Spatial locality, which is the fact that the address of the next location to be accessed in memory is more likely to be close to the address of the last location.
- Temporal locality, which is the fact that of a location has been accessed recently, it is likely to be accessed again.

These patterns appear in things like loops and linear iteration.  If the CPU instead tended to access random areas of memory, then a cache would likely actually be slower than a no-cache setup.

Caching is organized into blocks with some amount of words. For example, we might have a block length of 4 words, or 16 bytes. (assuming 32 bit/4 byte words)

On a cache miss, the cache loads an entire block from memory, which is how a cache exploits spatial locality.  

Since there are many blocks in main memory for every block in the cache, we need to keep track of where each block in the cache came from.  The cache does this by adding a **tag** to the block.  in addition, to keep track of which blocks have valid data in them, each block in the cache has a **valid bit**, which might be changed (for example) when the cache is emptied and reset.  
![[Attachments/Pasted image 20220418163231.png]]

A cache needs to decide where each block should go.  There are three common methods - direct mapped, fully associative, and N-way set associative.  

### Direct mapped
In a direct mapped cache, we take the main memory address and take its modulo relative to the size of the cache.  For example, if the cache has 8 blocks of 4 words, then it has a total of 32 words.  So when we get something from the main memory in a given location, we would take the main memory address, divide it by 4 (to get a block), and take its mod 8 to decide where it should go in the cache.  

Note that this is not a dictionary - this is only how we decide where the block should go in the cache.  To check for a hit or a miss, the cache compare the tag for the memory address with the tag stored in the cache, also checking the valid bit.  

For example, let's pretend that memory words are accessed in the sequence 3, 4, 5, 6, 32, 2, 3.

![[Attachments/Pasted image 20220418164032.png]]
Since the block containing memory address 3 isn't in the cache yet (since it was just reset), we need to load this into the cache. Since `(3//4)%4 = 0`, it ends up in block 0 of the cache.  

Then, memory address 4 isn't in cache.  So it loads the relevant block from main memory, and since `(4//4)%4 = 1`, it ends up in block 1 of the cache.  

Memory addresses 5 and 6 are both in block 1 (which stores addresses 4-7), so those are hits.  

Memory address 32 is clearly not in the cache, and so we need to load it from memory.  Since `(32//4)%4 = 0`, we end up overwriting the old block in the cache.  

Then, when we request memory address 2 again, block 0 no longer contains addresses 0-3, so a miss occurs in the cache needs to load the whole block again.  

It's evident that if you get unlucky, you might end up overwriting the same block of memory over and over again.  So is there a way to avoid this?  

### Fully associative mapping 
Fully associative mapping is where any memory block can be mapped onto any cache block. The cache is allowed to store blocks anywhere, but this comes at the cost of needing to check every tag on every memory access. Then, checking for a hit is slower, and also involves more bookkeeping on the block tags.  

This is typically not used, because the hardware to do this is expensive and slow.  

### N-way set associative mapping 
A way to improve our lookup times compared to fully associative mapping is to divide cache into sets with N blocks, such that when we check for a hit, the tags for all blocks in a single set are checked.  Then, memory addresses are direct mapped into a set.  

The net result is that we end up overwriting blocks less frequently, while also still retaining the faster search times for a given block.  

For example, if each block had 4 words and were stored in sets of 2 blocks, then the fixed mapping for every block in memory would mean that if we were to check for a hit, we simply check the tags for both blocks in that set.  

So for the same example as last time for direct mapped, when we access memory address 32, it is a miss and loaded into the cache.  Its direct mapping indicates that it belongs in set 0, but since we have a set size of 2, it can instead be loaded into block 0B instead of overwriting the memory block containing addresses 0-3, which is currently in block 0A.
![[Attachments/Pasted image 20220418165144.png]]

### Summary
![[Attachments/Pasted image 20220418164910.png]]

Worth noting is that 1-way set associativity is the same thing as direct mapped.  

Also, for a cache with B total blocks, then B-way set associativity is the same thing as fully associative (essentially, one set with a block count equal to the cache size).

Note that there are diminishing returns the bigger your set associative value is - given that the miss rate of a direct mapped cache is 20%, a 2-way associative cache is about 12%. But for every additional block you stick in a set, the complexity of hardware increases, while the hit rate improvement scales much more slowly.  
![[Attachments/Pasted image 20220418170543.png]]

Similarly, there's a sweet spot for block sizes. A block size that is too small means that you won't be able to take advantage of spatial locality, and will more likely to have misses.  

A block size that is too big makes it more likely that you'll be wasting cache space on words that are not needed.  Furthermore, when you need to load from the main memory, the penalty is increased because you have to load more memory.  

![[Attachments/Pasted image 20220418170707.png]]

## Quantifying the speed of a cached memory system
Given that we know $H$ is the hit rate, $T_{fast}$ is the cache access time, and $T_{slow}$ is the main memory access time, then the effective access time $T_{eff}$ is expressed as 
$$H*T_{fast}+(1-H)*(T_{fast}+T_{slow})=T_{fast}+(1-H)*T_{slow}$$
This is a linear function, so that if we theoretically had a 100% hit rate, the average access time would simply be equal to $T_{fast}$; if we had a 100% miss rate, the average access time would be equal to $T_{fast}+T_{slow}$.

As a result, if we have a high hit rate, then we've effectively created memory that's big, fast, and cheap.  

## Writing to memory
So far, we've only talked about reading from the cache/memory.  So what happens when we write to memory?  

If there's a hit for a given memory location, the cache can do one of two things:
- Write through, which means that we write the data to the cache and to the main memory
- Write back/copy back, which is where we write the data only to the cache, and wait until the block is removed from the cache to write it to main memory.  

Write back is notably better if we expect to write many times to the same block of memory before leaving it alone, so that we only have to write to the cache 10 times and then write it back to the main memory.  

If there's a miss for a given memory location, the cache can do two things again:
- Write the data directly to main memory 
- Load the block (just like for a read miss) and do either of the things mentioned for a hit

Either way, the goal is what's known as **cache coherence**, which is maintaining the same data in all copies of a memory as data values are written to the memory.  

## Cache levels
The last thing to note is that advanced systems usually use multiple levels of cache, often three levels connected in series.  

![[Attachments/Pasted image 20220418170807.png]]

These cache levels operate exactly the same way as individual caches hooked up to a single main memory.  

# Von Neumann vs Harvard architecture
Recall that when von Neumann built the ENIAC, he used an architecture where program and data were mixed in memory.  But at the same time, there was a team at Harvard that used separate memories for data and program.  

![[Attachments/Pasted image 20220418170949.png]]

Von Neumann architecture was very prevalent in the early days due to the expense of memory, and contines to be most common today.  But there are advantages to both.

## Harvard
![[Attachments/Pasted image 20220418171257.png]]
## von Neumann
![[Attachments/Pasted image 20220418171315.png]]

## Modified Harvard Architecture 

In a system with at least one level of cache, we can have the advantages of both architectures.  Here, the highest level of cache (closest to the CPU) has separate coaches for instructions and data, known as the Modified Harvard architecture.  

![[Attachments/Pasted image 20220418171425.png]]

# Growth of multicore processing 
About 15-20 years ago, CPU designers ran into a "speed limit" of sorts that caused CPU throughput to level off.  The greater the clock speed, the greater the frequency and the smaller the wavelength.  When the wavelength approaches the length of connections on a printed circuit board, then expensive circuit designs are required to support it. (This is because those waves start needing to be treated like radio signals, rather than conventional digital signals.)

In addition, because clock frequency is proportional to power, doubling the clock frequency would double the power required.  This isn't necessarily a hard-to-solve problem in itself, but the major issue is the power density; more power involves more heat, and the power density of a modern processor nearly approaches that of a nuclear reactor.  

The solution was to put multiple CPU cores on one chip, such that instead of having one CPU, you put several CPU cores on a big piece of silicon to spread the power dissipation out.  Each core has its own L1 and L2 cache, as well as instruction logic, an ALU, and load/store logic.  L3 cache was shard between all of the cores.  

The issue with this is that some processing tasks are not easily divisible such that they can all run at the same time.  But most desktops are well-suited for multicore processing, since you can just run distinct programs on each one.  

But the issue is that this makes cache coherence very difficult; if one cache gets a write, then all of the other cores need to know about the write.  All the cores could (in theory) need to write or read the same memory location at once, which requires cache coherence.  

This is achieved by **bus snooping** (or bus sniffing), in which each cache monitors all writes done to all coaches and ensures that any changes are propagated to all caches.

As a result of multicore processing, the space taken up by the L3 cache has grown considerably in size.  

# Virtual memory
One more layer in a memory hierarchy that can be used is virtual memory, which is mainly a feature of the OS.  Here, you use the hard disk to cache parts of memory, such that if the main memory fills up, it can swap chunks of main memory out to the disk.  
![[Attachments/Pasted image 20220420163212.png]]

If main memory runs out of space, the OS might identify a low-use process that can be placed into a page file in virtual memory.  Then, if the process becomes active again, the page can be taken from virtual memory.  

Of course, note that disk accesses are very slow compared to everything further down the line.  This fact, in combination with the increasing size of DRAM, makes virtual memory less necessary nowadays.  

# Summary of the memory hierarchy
![[Attachments/Pasted image 20220420163426.png]]
