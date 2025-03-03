# Rain-Rain-Go-Away
### *Group project, Kriti ’25, Inter-Hostel Technical Competition, IIT Guwahati*

AIM -  Design an automated rain  detection and wiper control mechanism that activates wiper rotation (0-180 degrees ) on detecting rain and displays four discrete controllable speed levels

Overall Circuit can be divided into 8 parts
1. ***Comparator Circuit*** - This circuit takes in the Analog output of the sensor and feeds it into the inverting input of  Op-amps. These Op-amps are each given a reference voltage from a voltage divider bridge that ranges from 3.7 V to ground (This is the rage of the sensor's analog output). When the sensor output drops below a certain level, the respective Op-amp will output a high voltage
3. ***Opamp Summer*** - Amplifies the digital output and generates analog output for different dicrete levels
4. ***Tri. Wave generator*** - This circuit consists of two parts. First part uses Opamp ckt to form a  square wave signal oscillating with a frequency of about 100 Hz. The second part of the circuit forms the integrator using an Opamp that uses the square wave from the first part to give a triangle wave
5. ***Comparator-PWM signal generation*** -  The triangle wave is fed into a comparator's inverting input, while the DAC's voltage is fed into the comparator's non inverting input.The resulting output of the comparator is a PWM signal whose duty cycle increases with increased output voltage from the DAC. Higher duty cycle causes the motor to rotate at a faster speed.  
6. ***Switch Circuit*** - We use two limiting switches to toggle the supply using dff and fed it to IN1 and IN2 to achieve proper wiper rotation(0 to 180 deg).
7. ***Motor Driver and Motor*** - This PWM signal is given to EN of motor driver, outputs from Switch Circuit to IN1 and IN2 and out1 and out 2 to a dc motor
8. ***Led and needles + Arduino*** -  We have used arduino UNO to control a servo motor that serves as the needle of speed indicator and the outputs from Comparator circuits is given to Leds which glows when the output is high and placed semicircularly to mimic speedometer.
