# WIRELESS-AC-LIGHT-DIMMER-WITH-BLUETOOTH
This project intails building a circuit that will enable the user to change the brightness of his or her home bulb via a mobile application using bluetooth connectivity.

### COMPONENTS USED
  1.	1N4007 (Rectifier Diodes)
  2.	RESISTORS
  a.	47K ohms (2pieces)
  b.	1k ohms 
  c.	100 ohms
  d.	200 ohms
  3.	240V AC Bulb
  4.	Microcontroller (Arduino Nano)
  5.	PC1817 (optocoupler)
  6.	BTA 16 (Triac)
  7.	MOC 3022 (Opto-Isolator)
  8.	HC-05 Bluetooth Module

### CIRCUIT DIAGRAM
![My Image](/Images/Circuit-diagram.png)

### OPERATION
  The circuit is divided into 3 parts
  1.	Zero Cross Detector Circuit
  2.	Phase/angle Control using Triac
  3.	Bluetooth Control the Dimming
  
### 1. Zero cross Detector Circuit
The AC voltage that we get from home supply is around 310 volts peak to peak or 220V RMS. The frequency is usually between 50-60Hz. We have a positive part and negative one so there will be a zero crossing. So, we will have to detect that zero-cross since our pulse needs to be in phase with the AC voltage

![My Images](/Images/Circuit-diagram2.png)

So, we have to detect when the voltage passes from positive to negative or from negative to positive and synchronize our pulse with that so it will fire always in the same spot. For that, we will use a full bridge rectifier. This will give the output both the positive and negative curves for the AC wave. The two 47k ohms resistors is to limit the current, to separate the high voltage side from the low voltage side, we will use EL817 optocoupler.

### 2. Phase/Angle Control using Triac
Using a component called TRIAC, we will control the amount of time that this power is ON and OFF. The TRIAC will remain deactivated until it receives a pulse at its gate. Once it receives, it will remain activated until the main input will change polarity. First, we need to detect the zero cross since the pulse needs to be in phase with the AC voltage. So we have to detect when the voltage passes from positive to negative and synchronize our pulse with that so it will fire always in the same spot.

### 3. Bluetooth to control the dimming
In order to control power, all we have to do is to control the timing between the zero cross and when fire the pulse at the TRIAC gate. So we will use UART communication through Bluetooth module to change the delay timing. The android app that is designed through MIT app inventor has a slider in it. Sliding the slider is like changing the value of delay serially through Arduino. The Arduino will map that value to delay between 1 and 10 milliseconds.

The android application will be connected to the hardware via Bluetooth module, after the connection is established one will be able to adjust the bulb brightness. The microcontroller function will be reading the values received from the Bluetooth module and instruct the relay to turn on or off, also it is responsible to control the TRIAC hence varying the bulb intensity by changing the phase angle.

### Images of The Project
![My Image1](/Images/Full-brightness.jpg)

#### Figure 1 Image of the bulb in full brightness

![My Image2](/Images/Low-brightness.jpg)

#### Figure 2 Image of the bulb in Low brightness

![My Image3](/Images/app.jpg)

#### Figure 3 image of the android application

### CONCLUSION
The project is very useful in real world applications since one is able to set the levels of brightness of the bulb which helps in reducing eyes problems caused by high brightness. Also, it makes one feel comfortable in a room.

