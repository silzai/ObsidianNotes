- It is the physical layer plus the data link layer reference/protocol models.
- Bandwidth: 
	- limits of how many bits can be transmitted (data rate)
	- A bandwidth needed to modulate, bandwidth needed for am is less than fm
- Throughput: 
	- Actual bits transmitted/time
- Goodput: 
	- amount of useable data that is transferred/time
- bandwidth: amount of data is allowed by the medium to flow during a given set of time

## Analogue: is the transfer of data in waves, we modulate then transfer the data
- modulation: 
	- we shift them to different intervals so waves do not interfere with each other, then the receiver will demodulate them
	- Amplitude modulation (am): We multiply the original frequency wave with a carrier frequency wave, to get (frequency/fluctuation will remain constant)
		- am is more error prone/sensitive to noise 
	- Frequency modulation (fm): We pass the original frequency wave to a VCO, that will (amplitude will remain constant)
## Digital: transfer in bits
- PCM (pulse coded modulation): 
	- technique to convert analogue to digital
	- If we actually want to represent waves digitally, we may need infinite amount of bits, but not possible
	- so we use sampling, where we take finite number of discrete points, and remove everything in between
	- then we can reconstruct the digital signal using those points, sampling frequency should be at least 2 fmax (fmax: maximum frequency of the original wave), so the sampling frequency $f_s$ will be: $$f_s=\frac{1}{T_s} greater than or equal to 2fmax$$
	- quantization: to store values that come in between, we can just take the value of the midpoint between the discrete points, and we will use 


	- first put the equality $f_s greater than or equal to2fmax$  
	- then will get $f_s$ samples/second
	- then will od 
	- then will multiply samples/second with bits/sample to get kb/s

## Methods for transmitting over wires:
- ASK: Transmitting a wave with a specific amplitude signifies whether it is a 0 or 1 bit
- FSK: Transmitting a wave with a specific frequency signifies whether it is a 0 or 1 bit
- Then for both, waves, we apply a phase shift $\phi$ to avoid errors, because both waves are at opposite positions, so can see whether a bit was off put from which original bit.
- we can add more points, but we use 

- with 
- with 
- With 16QAM, we can transfer 4 bits

- Signaling method: NRZ and Manchester encoding
- With long sequences, NRZ causes synchronization errors, so Manchester encoding is more safe as it will remain synchronized but it is more expensive as it needs more bandwidth

## Digital Transmission Over Copper Cabling
- Bit error rate is the probability of bit error: $$Bit\ Error\ Rate =\frac{number\ of\ bits\ in\ error}{Total\ bits\ transmitted}$$
- Occurs when we have original signal, and there is noise, and we have signal to noise ration where it is the ratio of both powers i.e. $SNR=\frac{P_s}{P_n}$, the higher the SNR, the better the signal, so $$SNR\propto \frac{1}{BER}$$
- do X_db = 10log_10X on both values of decibels, and get the values of X  
- then take the ratio of both Xs
- that ratio will be the 

- To have less bit errors, we can use:
	- UTP: length: 100m
	- STP: length: 100m
	- coaxial: length: 500m
	- fiber optic:
		- single mode: length: 100km
		- multi mode:  length: 2km

- Data Link Layer:
	- It communicates with the upper layers that are software, and also the lower layer, which is physical (hardware)
	- It is medium dependent
	- there are 2 sublayers in data link
		1) LLC sublayer: it interacts with upper layer, so does not care about hardware
		2) MAC sublayer: it need to know about the hardware in this, as it

- Trailer contains error detection information

- router/switch to pc: use straight through cable
- pc to pc: crossover cable
- will not draw the end devices that are connected to a hub, will just list the end devices ip numbers on the hub

- carrier sense multiple detection with collision detection, used by ethernet,  