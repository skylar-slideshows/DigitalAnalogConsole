Skylar - Digital/Analog Music Mixing Console / Gear
A music mixing console with a fully analog audio signal path (no DSP), managed by a digital control system.

The problem to fix
Historically, music recording studios relied on analog audio processing equipment. While digital signal processing has largely replaced it, many professional audio engineers still prefer analog hardware for its perceived superior sound quality. However, analog equipment lacks instant recall, requiring engineers to manually reset knobs and controls between projects. Since these knobs control actual resistances/potentiometers in the signal path, they need to be physically moved to the right place. In today's fast-paced production environment, where multiple sessions may be completed in a single day, this process can be time-consuming and impractical.

Proposal
My proposal is to design a set of basic audio engineering analog sound processors (an EQualizer, a dynamic range compressor, and volume control) with a digital system that uses “voltage controlled resistors” to allow recall to be handled by a microprocessor, making it instant. Instead of having moving knobs that are physical resistors, the knobs will only be digital rotary encoders for which a microcontroller calculates their relative position. The microcontroller then uses a control voltage to set resistors in the analog signal path to the value that a real knob in that position would be, making the signal path exactly the same “to the audio.” This would also allow the microprocessor to automate and adjust many parameters at once, which is another limitation with analog audio equipment. These three basic devices can be combined into one digitally controlled, analog “channel strip” that handles one layer of audio in the mix of a song. Many of these channels side by side, with a master section that combines all the signals, makes an audio console. This kind of technology is present in some standalone pieces of audio equipment, as well as parts of some synthesizers, but it has never been done at such a large scale.

Technical explanation
The “knobs” in our device (actually rotary encoders), send a digital signal with their relative position. To “scan” all the digital encoder “knobs” positions’, a microcontroller can be multiplexed to them, cycling through looking at all the knobs’ data outputs several times per second, meaning a few GPIO pins can be used to interface with many knobs. 


The microcontroller then calculates the value that a real potentiometer (based on its value and taper - linear? Log? anti-log?) would have in that same positon.


To make voltage controlled resistors that actually supply this resistance in the analog audio path, there are many approaches. A FET transistor has a “triode” or “OHMIC” region between when it is on and off, of high resistance, which varies by its gate voltage. As long as we stay away from the very edges of this region, the behavior is approximately linear (moreso on JFETs - Junction Field Effect Transistors) making them suitable for audio.
Another way is with OTAs (operational transconductance amplifiers), which are voltage controlled current sources. Since resistors themselves turn voltage into current, OTAs are essentially like resistors for our purpose.


For a non-continuous controllable resistor, we can use a network of many resistors in series and parallel, with transistors (electronic switches) between them to connect them in various ways that can produce an equivalent resistance through the entire network of essentially any value we want. There are premade chips for this. (resistor ladders)


We need to make sure that however we control the components, it does not get in the way of making a highly linear (low harmonic distortion), high fidelity (flat frequency response between 20Hz and 20kHz) audio path - i.e. making a good sounding piece of equipment that doesn’t distort the sound.
