Digital/Analog mixing console:

## More developed idea
- Clear goal/pathway to developing a finished project
- Covers areas of analog and digital electronics, some control systems, and software

## Room for development (what can 6 people spend several months on if this idea is already developed)

### Analog

#### Volume sliders
Voltage-controlled amplifiers: 
2x per channel, 32x total (16 channels)
  
#### Power Supply
+/-18V rails through a linear power supply for clean signal (min. ~15W) 
+3.3V clean reference for DACs in digital circuit (\~1W) 
+3.3V rail for digital electronics (\~20W) (isolated from clean ref. to prevent noise) 
+5V rail for LEDs 

#### Equalizer
State variable filter 
Control voltage comes from amplified DAC signal 
Op amp circuit to amplify DAC signal to control voltage for OTAs 

#### Pan
L/R VCAs for each channel 
Control voltage(s) come from DAC signal  

#### Toggle buttons (Mute/Solo)
Debounce circuit 
Button LED 
Software toggle to allow software control 

#### Insert points
Between each channel and the summing bus (pre- or post-fader option) 

#### Sends
Auxiliary busses

#### Master Section
Summing bus
AUX returns
Large screen
Master bus insert

#### Compressor

### Digital

#### Faders (motor-driven slide potentiometers)
Read by ADC on the chip 
Abstracted into something servo-like 
VCAs are controlled from software based on reading of faders 

#### EQ/Pan knobs
Rotary encoders 
LED ring 

#### Screens

### Software
(generally controlling all of the digital parts)
