- ***ambiguous chapter, so not completed***
- This chapter is divided into ==???????????????== parts:
	1) physical transmission of digital data
	2) Frame encoding technique

- The network access layer is the physical layer plus the data link layer in the reference/protocol models.

- 
## Analogue: is the transfer of data in waves
- we modulate the wave then transfer the wave (wave representing data)
- modulation: 
	- we shift them to different intervals so waves do not interfere with each other, then the receiver will demodulate them
	- Amplitude modulation (am): We multiply the original frequency wave with a carrier frequency wave, to get (frequency/fluctuation will remain constant)
		- am is more error prone/sensitive to noise 
	- Frequency modulation (FM): We pass the original frequency wave to a VCO, that will (amplitude will remain constant)
	- A bandwidth is needed to modulate waves and the bandwidth needed for AM is less than FM
	- FM and AM do not contain bits that are transferred, it is something else
## Digital: transfer in bits
- Suppose we have an analogue signal, and want to convert it into digital:
	1) sample the analogue signal
	2) Do PCM on the sampled signal
- PCM (pulse coded modulation): 
	- technique to convert analogue to digital
	- If we actually want to represent waves digitally, we may need infinite amount of bits, but not possible
	- so we use sampling, where we take finite number of discrete points, and remove everything in between
	- then we can reconstruct the digital signal using those points
	- sampling frequency should be at least $2f_{max}$ ($f_{max}$: maximum frequency of the original wave), so the sampling frequency $f_s$ will be: $$f_s=\frac{1}{T_s} \ge2f_{max}$$
	- quantization: to store values that come in between, we can just take the value of the midpoint between the discrete points, and we will use 


	- first put the equality $f_s \ge 2f_{max}$   
	- then will get $f_s$ in samples/second
	- then will od 
	- then will multiply samples/second with bits/sample to get kb/s

references: 
[njit edu on channel capacity](https://web.njit.edu/~joelsd/signals/classwork/BME314signalscw16.pdf)
and slides
## Methods for transmitting over wires:
- PSK modulation is used to actually transfer bits in waves (used in Wi-Fi).
	- BPSK
	- QPSK
	- 
- ASK: Transmitting a wave with a specific amplitude signifies whether it is a 0 or 1 bit
- FSK: Transmitting a wave with a specific frequency signifies whether it is a 0 or 1 bit
- Then for both, waves, we apply a phase shift $\phi$ to avoid errors, because both waves are at opposite positions, so can see whether a bit was off put from which original bit.
- we can add more points, but we use 

- with 
- with 
- With 16QAM, we can transfer 4 bits, more robust then PSK

- Signaling method: NRZ (non-return to zero) and Manchester encoding
- With long sequences, NRZ causes synchronization errors, so Manchester encoding is more safe as it will remain synchronized but it is more expensive as it needs more bandwidth

## Digital Transmission Over Copper Cabling
- Bit error rate is the probability of bit error: $$Bit\ Error\ Rate =\frac{number\ of\ bits\ in\ error}{Total\ bits\ transmitted}$$
- It occurs when we have original signal, and there is noise, we obtain a signal to noise ratio, where it is the ratio of the powers of signal and noise, the higher the $SNR$, the better the signal, so, $$SNR=\frac{P_s}{P_n} \quad and \quad SNR\propto \frac{1}{BER}$$
- Then to find the $SNR_{db}$ we have to solve this equation:$$SNR_{db} = 10 \times log_{10}(SNR)$$
- We can use this against the $BER$ to $SNR_{db}$ table to find what the $Bit \ Error \ Rate$ is against a value of $SNR_{db}$ 
- So the $BER$ vs $SNR_{db}$ graph, we can read the graph in two ways according to our requirement:
	- given a $SNR_{db}$, find the $BER$ for a particular modulation scheme (i.e. for QPSK or 16QAM)
	- given a $BER$, find the $SNR_{db}$ for a particular modulation scheme

- Bandwidth: 
	- is the amount of bit that can be transmitted over a medium during a given time (i.e. kb/s, Mb/s, Gb/s, etc.) "theoretically".
- Throughput: 
	- Actual bits transmitted/time (same as bandwidth) but
	- bandwidth is "theoretical", throughput is the "actual" data transmitted per unit time 
	- throughput is always less than the bandwidth because of 3 factors:
		1) Latency by network devices connecting the media
		2) Bit errors due to communication imperfections
		3) Frame collisions due to simultaneous transmissions
- Goodput: 
	- amount of useable data that is transferred/time

>***to avoid confusion:***
>- Throughput is how the rate of raw data you can stuff down a transmission medium without error.
>- Goodput is the rate of ”good data” absorbed and processed by applications, essentially meaning the throughput minus the rate of useless junk arriving.
>- “Useless junk” includes superfluous retransmissions, packets arriving too late to be useful, queue overruns, and any other discardable data arriving at the network interface.



- To have less bit errors, we can use:
	- UTP: length: 100m
	- STP: length: 100m
	- coaxial: length: 500m
	- fiber optic:
		- single mode: length: 100km
		- multi mode:  length: 2km

## Data Link Layer:
- It communicates with the upper layers that are software, and also the lower layer, which is physical (hardware)
- It is medium dependent
- there are 2 sublayers in data link
	1) LLC sublayer: it interacts with upper layer, so does not care about hardware
	2) MAC sublayer: it need to know about the hardware in this, as it

- In a frame:
	- Trailer contains error detection information (FCS: frame check sequence)

- In layer 2, a PDU takes different Frames on different media

- Will need to memorize the frame structures of these data link protocols:
	- Ethernet: 
		- The header is the preamble (synchronizes sending and receiving devices for frame delivery) of 8 bytes and trailer is FCS of 4 bytes and different number of bytes for PDU in between 
		- FCS has a value, used to check for damaged frames
	- point-to-point (its a common data link protocol for WANs): has a header flag of 1 byte and trailer FCS of 2 or 4 bytes
	- Wi-Fi: no need to memorize for this

- If a device sends request on a bus, then every device on the bus will get and check the frame, on a switch, everyone will not get the frame, because the switch will forward the frame only to the device with the specified MAC address.
- router/switch to pc: use straight through cable
- devices of same type (example, connecting pc to pc): crossover cable
- will not draw the end devices that are connected to a hub, will just list the end devices ip numbers on the hub

-  CSMA/CD: carrier sense multiple access with collision detection, used by ethernet, but we don't need this if we are using switch, since it will become the switches responsibility to forward frames and finish collisions between different devices
- The switch has a switching table 

- 