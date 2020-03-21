Increasing tension across the borders cause many conflicts among countries and India, Sri Lanka is no exception. The sea border between countries is not easily identifiable. The problem of Indian fishermen unintentionally crossing the border and getting abducted remains unsolved. Further, the inevitable harsh climate and the path misleading has cost many lives. Based on a census, so far in 2017, 215 Indian fishermen have been apprehended. About 30% of the fishermen family has lost their beloved ones. This instructable tends to describe the role of various surveillance technologies such as radar, unmanned aerial vehicles, satellites that can play to avoid chaos.

We can design an embedded system that notifies the fishermen about borders using GPS (global positioning system). We use the GPS receiver to find the location of fishermen and the longitude, latitude values are sent to micro-controller. The fishermen are alerted a few meters before the borders. On further moving the engine will stop.

In this instructable, I will be showing you how to do the fisherman border alert system using Arduino. This was just a short introduction, everything else from theory, building, and programming will be explained in later steps.

Supplies:
Parts list:

Arduino-Uno
GPS Neo-6M
General parts:

1 LED
1 Buzzer
1 DC motor
Male to male wires
Femal to female wire
Male to female wires
Double side tape

Tools:
Soldering Iron

Step 1: The Principle:
How can this project prevent fishermen? it gets the current location from GPS and alert the fishermen by comparing the live location with the predefined border.it works by using a major input current location of the boat using GPS. the first challenge is GPS and Arduino interface.

How does the GPS works?

Any instant of time, there are at least 4 GPS satellites in line of sight to a receiver on the earth. Each of these GPS satellites sends information about its position and the current time to the GPS receiver at fixed regular instants of time. This information is transmitted to the receiver in the form of a signal which is then intercepted by the receiver devices. These signals are radio signals that travel with the speed of light. The distance between a GPS receiver and the satellite is calculated by finding the difference between the time the signal was sent from the GPS satellite and the time the GPS receiver received the signal.

Once the receiver receives the signal from at least three satellites, the receiver then points its location using the trilateration process. A GPS requires at least 3 satellites to calculate 2-D position(latitude and longitude on a map). In this case, the GPS receiver assumes that it is located at the mean sea level. However, it requires at least 4 satellites to find receivers 3-D position(latitude, longitude, and altitude).
Step 2: What Is Arduino?

Ok , now you have the current location which was the major input. now you have to interface the Arduino with GPS before that you need to know about Arduino which is a microcontroller.

Arduino’s processor basically uses the Harvard architecture where the program code and program data have separate memory. It consists of two memories- Program memory and data memory. The code is stored in the flash program memory, whereas the data is stored in the data memory. The Atmega328 has 32 KB of flash memory for storing code (of which 0.5 KB is used for the bootloader), 2 KB of SRAM and 1 KB of EEPROM and operates with a clock speed of 16MHz.

The Arduino Uno power supply can be done with the help of a USB cable or an external power supply. The external power supplies mainly include AC to DC adapter otherwise a battery. The adapter can be connected to the Arduino Uno by plugging into the power jack of the Arduino board. Similarly, the battery leads can be connected to the Vin pin and the GND pin of the POWER connector. The suggested voltage range will be 7 volts to 12 volts.

Input & Output:
The 14 digital pins on the Arduino Uno can be used as input & output with the help of the functions like pinMode(), digitalWrite(), & Digital Read().

Pin1 (TX) & Pin0 (RX) (Serial): This pin is used to transmit & receive TTL serial data, and these are connected to the ATmega8U2 USB to TTL Serial chip equivalent pins.

Pin 2 & Pin 3 (External Interrupts): External pins can be connected to activate an interrupt over a low value, change in value.

Pins 3, 5, 6, 9, 10, & 11 (PWM): This pin gives 8-bit PWM o/p by the function of analogWrite().

SPI Pins (Pin-10 (SS), Pin-11 (MOSI), Pin-12 (MISO), Pin-13 (SCK): These pins maintain SPI-communication, even though offered by the fundamental hardware, is not presently included within the Arduino language.

Pin-13(LED): The inbuilt LED can be connected to pin-13 (digital pin). As the HIGH-value pin, the light-emitting diode is activated, whenever the pin is LOW.

Pin-4 (SDA) & Pin-5 (SCL) (I2C): It supports TWI-communication with the help of the Wire library.

AREF (Reference Voltage): The reference voltage is for the analog i/ps with analogReference().

Reset Pin: This pin is used for reset (RST) the microcontroller.
Step 3: The Design:
Take a cardboard and fix the Arduino at the centre so it is easy to connect all other devices. Use double side tape to fix a breadboard in front of Arduino on the side of digital pins. fix the buzzer near to the breadboard as shown figure. and place the GPS on another side opposite to the buzzer and also place a GSM module near digital pins.

Arrange according to your design but make it efficient to reduce the usage of wires.
Step 4: Connection of Arduino UNO and GPS Module:
GPS module has an antenna and fix it to the pin on GPS just push and lock it. Connect the four pins from UBLOX to an Arduino as follows:

GPS module ==> Arduino

GND ==> GND

TX ==> Digital pin (D0)RX of Arduino

RX ==> Digital pin (D2) or Tx of Arduino

Vcc ==> 3.3 V

TX and RX pins of GPS are connected to any digital pins of Arduino based on the pin that you are declared in your program.

Use prolific USB TTL to work by interfacing directly with your PC or computer. Using command prompt we can check whether it is working or not.

One more thing I have found while working with GPS antenna comes with the module is it is not receiving signal inside the house so I used this antenna. https://linxtechnologies.com/wp/product/sh-series... connecting this antenna, you have to use a connector.

One more thing is you have to be in open space when you interface for the GPS first time. be patient and wait for few minutes at first connection when it gets powered the led will blinks a second and when it got connected with the satellites it will blink continuously.it may take maximum 15 minutes for connection during first time interfacing if you couldn't get the LED blinking then there will be a problem on that model so it is good to exchange as soon as possible. please buy any module or sensor only after checking.
Step 5: Connecting Buzzer:
A buzzer has two wires as Vcc and GND.

it can work in 3.3V so u can connect it with one of the digital pins.

Buzzer VCC => Digital pin 8(D8)

GND => GND

you can use both Digital and Analog GND pins there is no difference. you can also use any of the Digital pins as GND by declaring itself as GND in your program as LOW or 0.
Step 6: Connecting Motor:
Usually, a Relay or Transistor can be used to switch a motor or OFF a motor using Arduino. But I did it without using them I just switch it by the digital pins itself. I connected one of the motor's PIN to the VCC 5v which is the power supply to the motor.

I connect another wire of the motor which has to be connected to the GND. But here I connected the GND wire of the motor to the digital pin10(D10) after declaring the pin 10(D10) as GND in my program I switch ON the motor using this D10 by making it as GND (LOW or 0) and I switch OFF the motor using the same pin D10 by giving HIGH or 1.when I give HIGH signal or 1 to the pin D10, so the motor will stop because of the absence of GND signal.
Connecting LED is just for an indication of whether it is near to the border or not.

Connect the positive terminal of the LED to the Digital pin 11 (D11).

Connect the negative terminal of the LED to the GND pin.
Step 8: The Program:
I had fun writing this program. It is very simple which contains only if-else loops. The program is done in Embedded C using Arduino software. the software link is attached below:

Arduino IDE Software

It requires two library files;

SoftwareSerial.zip

TinyGPS.zip

Install Arduino software and Include the above Zip files and start coding. the code contains the fixed the longitude, latitude to which the current location is compared. Arduino code has two parts:

Void Setup(): where you can initialize the Pin modes

Void Loop(): The code inside this loop runs indefinitely.

During explanation the variation maybe within a few meters so the last decimal itself to be considered so approximate the value given by the GPS to show variance in meters. and the values returned by the GPS are latitude, longitude, altitude, direction, no of satellites connected but here we need only longitude and latitude. they are in float datatype.

