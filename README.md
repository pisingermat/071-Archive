# 071-Archive
Archive for my 22.071 Final Project

This project aimed to design and build a tunable AM radio receiver. 
Ultimately, the circuit that was built unable to detect signals from radio stations. However, a transmitted 3.6kHz square wave test signal that was modulating a 1MHz carrier wave was audibly detected.

At it's core, the most general receiver is composed of four components, each with a very specific role:
1) The antenna 
The antenna collects energy from the radio waves that are travelling through the air and turns it into a small electrical signal. The radio waves are all oscillating at different frequencies, but the antenna effectively detects all of them. In this circuit we use a loop antenna to detect the magnetic fields. 
2) The bandpass filter (also known as a "resonator")
The bandpass filter then specifically selects the frequency we would like to listen to by resonating at that frequency, while reducing the effects and noise from all other frequencies. This component is what actually "tunes" the radio when you listen to different stations. In this circuit we use a simple LC circuit as the resonator. 
3) The demodulator
The demodulator extracts the audio signal from the carrier wave. Because the carrier waves are at such high frequencies the demodulator is important to prevent any issues with the impedance of the op-amp that comes later in the amplifier circuit. In this circuit the demodulation step is done by a diode in series with a RC circuit.
4) The amplifier
The amplifier increases the energy of the received and demodulated signal to make it detectable by an oscilloscope or audible through a speaker. In this circuit we use a non-inverting amplifier with a gain of 100.

The components used in this project are:
Antenna:
- ~2m of copper wire wound into a circle
- ~1.5m of copper wire wound around a plastic straw

Resonator: 
- 140 uH inductor, manually wound around a ferrite core
- 16-415 pF variable capcitor
* Based on this, the theoretical effective frequency range of this circuit is 660 - 3360 kHz.

Demodulator:
- 1N60A  Diode
- 10 MΩ resistor
- 22 pF capacitor

Amplifier:
- LF 411CN Op-Amp
- 100 kΩ resistor
- 10 kΩ resistor
- 1 kΩ resistor

The circuit diagram ultimately used in this project is in the repository, both labeled and unlabeled versions. As well as a labeled and unlabeled image of the actually constructed circuit.

A couple things to note:
- The antenna is coupled to the resonator via inductancive driving of the 140 uH inductor. The antenna coil and the inductor are set up in a coaxial configuration design.
- The 10 kΩ resistor that jumps to ground from the V+ lead of the op-amp is there to eliminate bias currents as there were some voltage drift problems in the amplified signal. 
- The 51 Ω resistor connected to the output of the op-amp is there to protect the speker that was used to listen to the detected signals. 

Possible issues to explore and troubleshoot the product:
- The amplifier gain is too low. This means that any faint signals would be simply detected as noise.
- The pass band from the resonator is too narrow or broad. This means that too much or too little of the desired signal is being properly detected. A Bode plot of the circuit is needed to accurately determine this.
- Antenna is not picking up enough signal. This means the antenna is too small, which reduces the amount of signal that is picked up overall. It could be helpful to explore tuned antennas instead. 

*It is unclear if these problems are the immediate cause of the radio being unable to detect signal. These were just some things that I thought could be the problem. 