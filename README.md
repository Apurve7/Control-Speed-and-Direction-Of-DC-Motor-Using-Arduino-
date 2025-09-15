# Control-Speed-and-Direction-Of-DC-Motor-Using-Arduino-

This project controls the speed and direction of a DC motor using an Arduino, a potentiometer, and two push buttons. It requires an L293D motor driver IC to function.

Functionality ⚙
This program allows for precise control over a standard DC motor.

Speed Control: A potentiometer connected to an analog input (A0) is used to set the motor's speed. The code reads the potentiometer's value (0-1023) and maps it to a PWM signal range (0-255) using the map() function. This allows for smooth speed adjustment from a dead stop to full power.

Direction Control: Two push buttons, configured with internal pull-up resistors, determine the motor's direction.

Pressing the "forward" button (pin 13) makes the motor spin in one direction.

Pressing the "backward" button (pin 12) makes it spin in the opposite direction.

If no button is pressed, or if both are pressed, the motor will not run.

Motor Driver Logic: The Arduino doesn't power the motor directly. Instead, it sends PWM (speed) and direction signals to an H-bridge motor driver IC (like an L293D). The code sends the motorValue (speed) to one of the IC's input pins and a direction signal to the other, causing the motor to turn.

Control Delay: A delay(500) is included in the main loop, meaning the controls will only update every half a second. This will result in a noticeable lag between turning the potentiometer or pressing a button and the motor's response.

Hardware Requirements 🔩
Arduino Uno (or compatible board)

1x DC Motor

1x H-Bridge Motor Driver IC (e.g., L293D)

1x 10kΩ Potentiometer

2x Push Buttons

External Power Supply for the motor (e.g., 9V battery or DC adapter)

Breadboard

Jumper Wires

Software Requirements 💻
Arduino IDE

Circuit and Connections 🔌
Warning: Do not power a DC motor directly from the Arduino's 5V pin. Always use an external power source connected through a motor driver.

Control Components:
Component	Connection
Potentiometer (Middle Pin)	Arduino Pin A0
Potentiometer (Outer Pins)	Arduino 5V and GND
Forward Button	Arduino Pin 13 and GND
Backward Button	Arduino Pin 12 and GND


Motor Driver (L293D Example):
Arduino Pin	L293D Pin	Function
Pin 11	Pin 2 (Input 1)	Controls motor direction
Pin 10	Pin 7 (Input 2)	Controls motor direction
5V	Pin 16 (VCC1) & Pin 1 (Enable 1,2)	Logic Power
GND	Pins 4, 5, 12, 13	Ground


Motor and Power:
Connect the two terminals of your DC Motor to the L293D's output pins (Pin 3 and Pin 6).

Connect your External Power Supply positive (+) to the L293D's Pin 8 (VCC2).

Connect your External Power Supply ground (-) to the Arduino's GND pin (this creates a common ground).

