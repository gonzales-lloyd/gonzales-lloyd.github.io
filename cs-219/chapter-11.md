Computer organization is the "hardware designer's model" of the CPU, also called microarchitecture.  Some people may use architecture and organization interchangeably, but formally, these are two different things.  

We've spent some time looking at how a CPU operates, but it's now time to move onto memory.  Clearly, if the memory interface's speed or its bandwidth isn't enough, optimizing the CPU is pointless. If memory doesn't keep up with the CPU, then CPU speedups are considerably reduced.  

This is a fairly significant problem in modern computing, where the CPU had improved considerably, but memory hadn't improved nearly as much. This is where bottlenecking comes into play - we weren't able to have memory interfaces keep up with CPUs.  

Also worth noting is that CPU throughput hasn't increased in about twenty years; obviously CPUs are still faster than they were back then overall, but it's important to note that modern CPUs have tended towards multicore processing than performant single-core processing.  So the sum of a CPU's parts is stronger than it was twenty years ago, but the individual cores haven't gotten much faster.  

# Memory types
There are a few kinds of memory types.  There are non-reprogrammable memories, like ROM (read-only memory) and PROM (programmable read only memory). There are also programmable memories.

That said, memory ICs have very similar interfaces; they have an input address, a read/select bit, and a data output. Depending on whether it's read-only or not, it might also have a "write enable" control input.  

Internally, memory is organized as a 2d array where the horizontal lines (or wires) are address/word lines and the vertical lines are bit lines.  Then, each address' memory has its full word (32 bits, in our case) on each row, and each bit lies on each vertical space. A memory element connects the wires at each intersection, where each wordline corresponds to one address and each bitline corresponds to one bit of the word.

![[Attachments/Pasted image 20220413160737.png]]

## Read-only memory (ROM)
Read-only memory has is hardwired into the IC, and has a high fixed cost, such that changing the data requires changing a mask layer.  But if you are making an IC, then it's almost free to add a ROM; the cost is very low, and is often used in a chip that has other digital circuits.  

## Programmable ROM (PROM)
Programmable ROMs are similar to ROMs in that (after production) they are read-only, but can be programmed by an end-user with an inexpensive programming machine.  They are programmed by blowing or keeping fuses at each bit location to store 1s or 0s:
![[Attachments/Pasted image 20220413161741.png]]
And it's clear that if you blow a diode, it's gone forever.  Therefore, PROMs can really only be programmed once into ROM, but they are very effective for prototyping and are relatively cheap.  

## EPROM 
EPROMs are erasable PROMs, whhich use floating gate transistors as a memory element.  In essence, you can put a charge on each transistor which effectively stores a bit in each transistor.  You can "unprogram" all of the bits by exposing the EPROM to concentrated UV light, so that the device can be reprogrammed.  You will likely have a specialized machine to put the chip into, and over time, the charge on gates dissipate.  

Microcontrollers can include EPROM, and are typically used for development and low-volume applications.  

## EEPROM
EEPROMs are electrically-erasable PROMs, which mean that you can reprogram them using electric impulses (without placing it in a UV booth). In other words, this is flash memory.  EEPROMs also use floating-gate transistors as a memory element, but can be reprogrammed without using an eraser and a programmer - you just need to send electrical signals.  

# Flash memory 
Fujio Masuoka is credited with inventing flash memory as an unauthorized project that he did in his spare time. He developed memories and high speed circuits at Toshiba from 1971-1994, and Toshiba would ultimately ignore Fujio's idea.  Intel would be the first to market it in 1988.  

Flash memory is named that way because the process of erasing the memory remind him of the flash of a camera.  

Flash is notably lower cost than EEPROM, but has a shorter reprogramming life and take a considerable amount of time to erase.  These are often used for code and large data sets, having a parallel interface.  Because you have to reprogram entire sectors at a time, it takes much longer to erase, and makes it more difficult to target specific parts of memory.  

EEPROMs are more expensive (having two transistors per bit than one transistor for flash), but can undergo much more reprogramming cycles and can also have targeted memory reprogramming.  These have a serial interface and are typically used for smaller amounts of data. 

## Flash sectors
Flash memories are divided into sectors, which must be programmed one sector at a time.  If there is at least one 0 bit that must be programmed to a 1, the entire sector has to be erased and then rewritten.  

## Flash types
There are two types of flash: NOR flash, and NAND flash.  

NAND flash has the smallest physical bit cell size, and requires bytes to be accessed sequentially.  

NOR flash is slightly larger, but bytes can be accessed randomly.  Furthermore, it has faster read speed.  However, it has slower programming speed, lower memory density, and a higher cost per bit.  It does live longer than NAND flashes in that it can handle more erase cycles.  

NAND flash is more commonly used for data/file storage, as in flash drives and SSDs due to its higher memory density; NOR flash is more commonly used for code, due to its higher read speed and frequent erases.  

(Since you only ever write to flash when you're trying to program it, it's also correct to refer to programming speed as write speed.)

Here's a general overview of memory technologies:
![[Attachments/Pasted image 20220413163514.png]]

# RAM
There are two kinds of RAM: static ram, or SRAM, and dynamic RAM.  Conceptually, RAM is similar to a register file - it's a set of memory locations that we can read or write to.  

Each bit in SRAM is usually implemented in silicon using what's known as a 6-transistor or SRAM cell.  It was invented at Fairchild Semiconductor in 1964.  The inverters are connected for positive feedback, retaining the data value into the cell, and have a weak drive state.  To write a new value to a bit, a strong driver circuit forces the inverters to change state.  

SRAM is called static because it holds memory as long as it's powered on, after the inverters have been programmed.  

In contrast, each cell in DRAM is one transistor and one capacitor.  Each cell is much smaller, and allows more bits per unit area on an IC.  However, the capacitors leak over time, and the memory cells have to be continually recharged to hold their values.  

![[Attachments/Pasted image 20220413164422.png]]

DRAMs were invented by Rober Dennard in 1966 at IBM, and although others were skeptical of the idea, DRAM was in virtually all computers by the mid-1970s.  

To make SRAM or DRAM, cells are connected in a 2D array.  Address decoders select individual rows and columns, such that if there are 4096 memory locations, 12 address bits are needed with 6 address bits selecting rows and 6 bits selecting columns in a 64x64 array of cells.  
![[Attachments/Pasted image 20220413164529.png]]

That said, even though we do need to refresh DRAM regllry, the overhead for doing so is relatively small.  Refreshing might take 100 nanoseconds; rows might need to be refreshed every 50ms to avoid data loss.  Thus, only about 3.3% of the total bandwidth is lost.  

DDR, double data rate, has became the most common DRAM. DDR transfers data on both the rising and falling edges of the system clock, rather than SDR (single data rate), which only transfers data on the rising edges of the system clock.  There is, of course, a limit to how fast we can clock a digital circuit; the faster the clock frequency, the more power you need to supply.  Over time, DDR generations have had faster clock rates, transfer rates, and bandwidths, with each generation approximately doubling max speeds.  

SRAM has bigger cells, is more expensive than DRAM, and uses more power per bit, but has faster access time and does not need refreshing.  They use CMOS processes, which means that they can be placed directly onto an IC.  However, DRAMs have a unique fabrication process, and are practically always supplied as separate ICs.  

# Error detection 
Volatile memory in memory systems sometimes have error detection or error correct added as a feature.  This was originally added to DRAMs because the refresh process could fail; furthermore, soft errors could occur, which is when radiation causes a voltage change inside a RAM.  

This has become more important over time, since as transistors have became smaller, they have become much more susceptible to particle strikes.  It's been found that soft errors in DRAMs are not uncommon; and although less common, SRAMs are also prone to errors.  

One way to do error detection is through the use of parity bits, which tell you if the number of bits in a word or byte is even or odd.  Error correcting codes, such as Hamming codes, can also be used.  

# Making big memory systems 
Individual memory ICs are often combined with a little glue logic to make a larger memory.  Even if individual chips can support only 128kb, it's possible to combine many of them to make wider buses or larger total memories.  This is fairly common.  


# Relative costs
![[Attachments/Pasted image 20220413165706.png]]

# Hard disks/drives
Hard disks are also a memory technology, in which they use mechanical parts to store and retrieve memory.  In the past, they were widely used because they were much cheaper and much larger (in terms of capacity) than solid state drives.  However, solid state drives have became much cheaper, and because they are much faster, are becoming increasingly common.  