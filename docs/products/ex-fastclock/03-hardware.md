
#Hardware

  
##What you need for EX-FastClock

* An EX-CommandStattion running version 5.0.0 or later
* An Arduino Uno microcontroller
* An MCUFRIEND type plug in shield TFT touchscreen
* A suitable power supply
* Dupont type wires to connect the components, male to female or female to female as required
* A USB cable to connect the Arduino to a PC to load the software

The software for the  EX-FastClock can be found in the  EX-FastClock repository in the DCC-EX GitHub.  The code can be configured to run a clock which will communicate to the Command Station by either Serial or I2C.  The options are chosen from the file config.h.  Instructions are contained in the README.md file.  Which option you choose will depend upon weather you have serial throttles connected to the serial ports in which case I2C might be the better option.  Alternatively if you already have lots of I2C devices then it might be better to run the Serial option.

Now that you know what you need, click the "next" button see how you use  EX-FastClock.