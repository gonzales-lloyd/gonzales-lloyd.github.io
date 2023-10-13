This chapter focuses on I/O, which includes peripherals and the interfaces we use to access them.  For memory, speed is a priority.  But for I/O, the priority is often extensibility, since it's a lot easier to swap out mice and webcams than RAM and CPUs.

I/O tends to be different for different kinds of computers; you might need a display, keyboard, USB, Ethernet, webcams, or maybe not.  

# USB
The most common peripheral bus is USB, or Universal Serial Bus.  Many years ago, there were different types of interfaces for internet, printers, keyboards, mice, and displays.  The goal with USB was to unify each of these interfaces. The standard caught on with the iMac in 1998, which used USB as its main external interface.  

The goal was to make connected devices easy to configure, such that they would be "plug and play." More of the interface was handled through software drivers.  Since it supplied 500mA of power to the connector, it could support more devices.  And finally, while previous interfaces might have been parallel or (low-speed) serial, USB's distinct serial interface required much fewer connections, making it simpler.  

USB uses what's known as low voltage differential signalling, or LVDS.  Rather than a single-ended signal, LVDS effectively provides for the complement of a given data signal on both lines, which allows data transfer to be much faster. LVDS is also used in Firewire and Ethernet connections.  

![[Attachments/Pasted image 20220420164403.png]]

When a USB host powers up or when a new device is connected to the bus, the host "enumerates" the devices and assigns one of three modes to them:
- interrupt, for devices like keyboards and mice that send data infrequently 
- bulk, like printers which receive data in one big packet; data is sent in 64-byte chunks with error detection 
- isochronous, for streaming devices that need data (like audio/speakers or video/displays) in real-time, with no error correction. This is much like UDP, where you don't want to wait for missing display frames since it doesn't make sense to.  

# I2C
I2C, or Inter Integrated Circuit, is a simple two-wire serial bus for connecting chips.  It was invented by Philips in 1982, and was widely used after the patient expired.  It's very inexpensive because the protocol is so simple; only two wires are needed, the SCL (serial clock) and SDA (serial data), so resulting chips can be tiny and cheap.  

The outputs are open-drain, which means that many devices can be connected to one bus.  Each device has its own address which is sent by the master, which is the main processor; slaves receive the data, and are typically non-computational devices like fans and temperature sensors.  

An I2C transaction starts with SDA and SCL high.  The master pulls the SDA low with SCL high, known as a start condition.  The master then sends out a servant address and a read/write bit, after which the servant sends an ACK or acknowledge bit.  The master sends the clock; then, for a write, the master sends data; for a read, the servant sends data.  A transaction ends with a NACK, or negative acknowledge.  

Here's a sample transaction:
![[Attachments/Pasted image 20220420165424.png]]

An I2C bus can operate at varying speeds.  The original standard operated at 100kHz; the fastest modes require additional design effort and are less commonly used, since they require more current and therefore more power.  The fastest mode, UFM, goes up to 5.0 MHz.

## SPI
Instead of using those modes, SPI is often used for faster data transfer.  There are three wires: the serial clock SCK, the master-out-serviant-in MOSI, and the master-in-servant-out MISO.  SPI was created in 1985 due to the patent over I2C.

Because of the separate data signals, SPI can go much faster than I2C (20 MHz), but doesn't have addresses.  To have different chips on the same bus, a separate chip select signal is used to select each device.  This is slightly more expensive and consumes more power, but is preferred over I2C when speed is needed.  
![[Attachments/Pasted image 20220420165847.png]]

An SPI transaction is where:
- the master asserts the correct chip select signal is LOW, which is used to "select" the device
- The master clocks out a command
- The master sends out clocks for the data, where the master clocks out data on MOSI for a write, and the servant sends data out on MISO for a read.  

![[Attachments/Pasted image 20220420170016.png]]

# UART
UART, or Universal Asynchronous Receiver/Transmittor, is a very old serial interface with a three wire interface - TxD, RxD, and ground.  This establishes a point-to-point connote between two devices, where either device can send data to the other at any time (and so there is no master or servant chip).

![[Attachments/Pasted image 20220420170127.png]]

Because the interface is asynchronous, there is no clock, so the bit rate has to be agreed on ahead of time.  (Well, there are clocks, but they're not synchronized.)

![[Attachments/Pasted image 20220425161423.png]]
Transactions are very simple; there's a start bit, 8 data bits, (possibly) a parity bit, and then a stop bit.  The wires are held HIGH unless data is being sent; the start bit is an initial LOW, and the end bit is a final HIGH.  

# Analog-to-digital converter 
An analog to digital converter, or ADC or A/D, converts an analog voltage to some proportional digital number.  Analog signals include voice and temperature, where the signal is (formally) continuous and not discrete.  

This process requires some analog reference voltage, which is the maximum analog volt that can be measured.  Generally, the digital output is equal to the ratio of the input voltage over the reference voltage, multiplied by the available digital range.  If the output of an A/D is 8 bits, then there are 2^8 possible levels.  

Of course, a digitized signal will always be imperfect; the more bits you use, the higher the A/D resolution.  
![[Attachments/Pasted image 20220420170843.png]]

So for example, if you have an 8-bit A/D (with a max of 256 resolvable values), if you have an input voltage of 0.7 volts and a reference voltage of 2.5 volts, the resulting output number is
$$\frac{0.7}{2.5}*2^8\approx 71.68 \rightarrow 72$$
where the immediate result of the multiplication is rounded to the nearest integer.  

The number of bits $n$ for $2^n$ possible values is known as the resolution of the A/D. So our A/D in the previous question has a resolution of 8 bits.  

# Modern networking
## Ethernet
Ethernet, or IEEE 802.3, was invented at Xerox in 1973 and was later released as a standard.  It originally operated at 10 megabits per second, and was a protocol based on the University of Hawaii's Aloha protocol.  Since running wires wasn't feasible across all of the university's buildings, they had to use radio links.  But clearly that means everyone might transmit at once, so a protocol was needed.  

Here, all the devices were connected to a common cable, where there was no master and no servant.  To send data, you listened to the signal on the cable; if nobody was transmitting, you were could start transmitting.  If there were no collisions, you could send your data; if there were collisions, you could wait for a random time and try again.  

![[Attachments/Pasted image 20220425162151.png]]

Over time, IEEE 802.3 has evolved to include 100 megabit per second and 1 gigabit per second variants.  Modern cables of 10 gigabits per second also exist now.  

Its high speed, low cost, and easy installation led to wide acceptance.  Because parts of Ethernet were included in the development of the internet, it is still widely used for networking. This has contributed to its long life; part of Ethernet got rolled into the internet, and this made it hard to abandon.  

## Wi-Fi
IEEE 802.11, or Wi-Fi, is currently the dominant wireless networking standard.  Most commercial wireless devices, like cell phones, TV, and radio, use radio frequencies licensed from the FCC and other regulatory bodies.  Ordinarily, if you want to broadcast a radio transmission, you need a license from the FCC, and you need to follow rules regarding interference and broadcasting power.  It also costs quite a bit of money to do this, since the band is so small.  

But Wi-Fi uses the industrial, scientific, and medical (ISM) bands, which allows unlicensed use for low-power transmitters.  This is a part of the electromagnetic spectrum where the FCC permits unlicensed use, so long as the power is sufficiently low (so that Wi-Fi doesn't go as far as radio, but is still useful.)

The main advantage of Wi-Fi is convenience over the regulated wireless communication methods.  Furthermore, the transmission medium is free; wires cost money, air does not.  

Like most standards, 802.11 is a family of standards with different costs and throughput, with varying frequencies and maximum linkrates.  

# I/O
Wired connects are generally faster than wireless.  Although wireless signals travel faster than electric signals in a wire, wireless signals are more susceptible to interference and have scattered energy.  They deteriorate much faster than a signal in a wire.  

But since Wi-Fi is fast and reliable enough, it's survived along with Ethernet.  

# Buses
In some sense, each individual "standard" works on its own bus. What's shown below is a system bus, which allows each component to talk to each other on an IC or computing component.  

![[Attachments/Pasted image 20220425163348.png]]

Bus standards transfer data on a motherboard or within an IC, with an example being the AMBA bus on ARM chips.  A standard includes signals/wires, a protocol, and possibly connectors.  Many deviecs can share the bus, such that there is no point-to-point connection.  

Data usually moves in parallel.  

Commonly, the bus width is the same as the CPU, so everything works at the same bit width.  (Note that DMA is direct memory access, a state machine that can move data in and out of memory without CPU reads and writes.) In essence, it allows things from one buffer to be moved to another buffer, without additional input from the CPU.  The DMA takes over the bus, works independently from the CPU, and then interrupts the CPU when it's done.  

# PCIe
Many modern systems have gradually been shifting over to PCIe, or Peripheral Component Interconnect Express.  It uses high-speed differential serial connects called lanes, where each lane sends one bit of data per transfer in both directions.  For higher throughput, you simply add more lanes.  Because it's on an IC, it's much faster than the also-serial USB.  

Devices that require higher throughput use more lanes; slower devices can also be combined to access the CPU through a bridge.  Memory has its own dedicated bus, and all devices on the bus can function as a DMA - an interesting property of PCIe.  This means that you can program them to send a block of data from any device to any device on the bus without CPU input or a dedicated DMA device.  

