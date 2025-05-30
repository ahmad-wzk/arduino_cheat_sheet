## What is Arduino?
Arduino is an open-source electronics platform based on easy-to-use hardware and software. Arduino boards are able to read inputs - light on a sensor, a finger on a button, or an Twitter message - and turn it into an output - activating a motor, turning on an LED, publishing something online. You can tell your board what to do by sending a set of instructions to the microcontroller on the board. To do so you use the Arduino programming language (based on Wiring), and the Arduino Software (IDE), based on Processing.

There are many different types of Arduino boards (e.g., Arduino UNO, Arduino Mega, Arduino Nano) designed for different needs and projects.

## Arduino Software (IDE)
The Arduino Integrated Development Environment (IDE) is a cross-platform application (for Windows, macOS, Linux) that is written in functions from C and C++. It is used to write and upload programs to Arduino compatible boards, but also, with the help of 3rd party cores, other vendor development boards.

**Key features of the Arduino IDE:**
*   **Code Editor:** For writing and editing your Arduino sketches (programs).
*   **Serial Monitor:** For communicating with your Arduino board over USB.
*   **Library Manager:** For easily adding functionalities to your sketches.
*   **Board Manager:** For installing support for different Arduino boards.

You can download the Arduino IDE from the official Arduino website: [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)

**Basic IDE Usage:**
1.  **Select your board:** Go to `Tools > Board` and choose the Arduino board you are using.
2.  **Select your port:** Go to `Tools > Port` and select the serial port your board is connected to.
3.  **Write your sketch:** Write your code in the editor.
4.  **Verify/Compile:** Click the checkmark button to compile your sketch and check for errors.
5.  **Upload:** Click the arrow button to upload your sketch to the Arduino board.

## Arduino Cheat Sheet
##### github.com/ahmad7428
## Comments
```
// This is a single line comment

/*
This is a
block comment
*/
```
## Variables
```
int any_variable = 58;
```
## Data types
```
byte a;      // 8-bit unsigned number (0-255)
int a;       // 16-bit signed number (-32,768 to 32,767) - default for most Arduino boards (like Uno)
unsigned int b; // 16-bit unsigned number (0-65,535)
long c;      // 32-bit signed number (-2,147,483,648 to 2,147,483,647)
unsigned long d; // 32-bit unsigned number (0-4,294,967,295) - useful for millis()
float e;     // 32-bit signed number with decimal points (approx 6-7 decimal digits precision)
double f;    // On Arduino Uno and other ATMEGA based boards, this is the same as float. On Due and other SAMD boards, this is a 64-bit number.
char g = 'A';// Stores a character value. Characters are stored as numbers (ASCII encoding). (e.g. 'A' is 65)
bool h = true; // Holds either true or false.
void         // Indicates no type; used for functions that return nothing or have no parameters.
```
Note: The size of `int` can vary depending on the Arduino board (e.g., 32-bit for Arduino Due).
## Arithmetic in Arduino
```
a = a + 2;	// Addition
b = b - 2;	// Subtraction
c = c * 2;	// Multiplication
d = d / 2;	// Division
```
## Comparison Operators
```
a == b 	  // a is equal to b
a != b 	  // a is not equal to b
a < b 	  // a is less than b
a > b 	  // a is greater than b
a <= b 	  // a is less than or equal to b
a >= b 	  // a is greater than or equal to b
```
## Logical Operations
```
x > 6 && x < 12   // AND operator
x > 6 || x < 12   // OR operator
!x > 6            // NOT operator
```
## Compound Assignments
```
x++       // increments by 1
x--       // decrmenets by 1
x += y 	  // increments x by +y
x -= y 	  // decrmenets x by -y
x *= y 	  // multiplies x by y
x /= y 	  // divides x by y
```
## Pin assignment
```
pin_1_name = 9;         // Assign a digital pin
pin_2_name = 3;
analog_pin_name = A0;   // Assign an analog pin
// Note: Actual pin configuration (setting mode as INPUT/OUTPUT) is done in the setup() function using pinMode().
```
## Pin Operations
```
pinMode(pin_name, INPUT);                     // Sets pin as Input. The pin is in a high-impedance state.
pinMode(pin_name, INPUT_PULLUP);              // Sets pin as Input and enables the internal pull-up resistor.
                                                      // This means when nothing is connected to the pin, it will read HIGH.
                                                      // Useful for buttons or switches where one state connects to GND.
pinMode(pin_name, OUTPUT);                    // Sets pin as Output

int digital_value = digitalRead(pin_name);   // reads a digital (discrete) value (HIGH or LOW) at the specified pin
digitalWrite(pin_name, HIGH);                 // sets the mentioned pin voltage level HIGH
digitalWrite(pin_name, LOW);                  // sets the mentioned pin voltage level LOW

int analog_value = analogRead(analog_pin_name); // reads an analog value (0-1023 for most Arduinos) at the specified analog pin
analogWrite(pwm_pin_name, value);             // Writes an analog value (PWM wave) to a PWM capable pin.
                                                      // Value is typically 0-255. Not all digital pins support PWM.
                                                      // (Previously, this line was: analogWrite(any_variable); which was incorrect)
```
## Structure
```cpp
#include</*any Libraries you want to call*/>

pin_declaration = 9;    // Pin Declaration
int a = 8;              // Initialising and Declaring any variables
// Global variables and constants are declared outside setup() and loop().

void setup(){
  // Initialization code runs once:
  // e.g., pinMode(pin_declaration, OUTPUT);
  // e.g., Serial.begin(9600);
  // statements;
}

void loop(){
statements;
}
```
## Setup (Runs once at the start-up)
```cpp
void setup(){
	pinMode(pin_name, OUTPUT); // Example: set a pin as output
}
```
## Loop (Keeps running until powered off)
```cpp
void loop(){
	digitalWrite(pin_name, HIGH);
	delay(1000);
	digitalWrite(pin_name, LOW);
	delay(1000);
}
```
## Functions
```cpp
// Functions allow you to structure your code into reusable blocks.
// A function can take parameters (inputs) and can return a value (output).

// Defining a function:
// returnType functionName(parameterType parameterName1, parameterType parameterName2) {
//   // code to execute
//   return value; // if returnType is not void
// }

// Example: A function that takes two integers and returns their sum
int addNumbers(int x, int y) {
  int sum = x + y;
  return sum;
}

// Example: A function with no return value (void)
void printMessage(char* message) {
  Serial.println(message);
}

// Calling a function:
void setup() {
  Serial.begin(9600);
  int result = addNumbers(5, 3); // result will be 8
  Serial.print("Sum: ");
  Serial.println(result);

  printMessage("Hello from function!");
}

void loop() {
  // You can call functions in the loop too
}

// Variable Scope:
// Variables declared inside a function are local to that function.
// Variables declared outside of any function are global and can be accessed from any function.
// It's generally good practice to keep variables in the narrowest scope possible.
```
## Conditions
```cpp
if (random_variable >= 55){
	digitalWrite(13, HIGH);
}
else if (random_variable <= 55){
	digitalWrite(13, LOW);
}
else{
	digitalRead(pin_name_2);
}
```
## Loops
```cpp
// For Loop
for (int i = 0; i < 50; i++){
	// This code inside for loop will be run 50 times
	digitalWrite(13, HIGH); // Turns Built-in LED ON
	delay(500);				// for 0.5 seconds
	digitalWrite(13, LOW);  // Turns Built-in LED OFF
	delay(500);				// for 0.5 seconds
}

// While Loop
while (pin_name_2 == 1){
	digitalWrite(13, HIGH);
}

// Do While Loop
do{
	digitalWrite(13, HIGH);
} while (pot <= 500);
```
## Arrays
```
// An array is a collection of variables of the same type, accessed by an index.
// Indices start at 0.

// Declaring an array:
int myInts[5]; // Declares an array of 5 integers (indices 0-4)
char message[] = "Hello"; // Declares a character array (string) and initializes it.
                                 // The compiler automatically calculates the size (6, including null terminator).

// Initializing an array:
int myValues[] = {2, 4, 6, 8, 10}; // Declares and initializes an array of 5 integers.
float sensorReadings[3] = {0.0, 0.0, 0.0};

// Accessing array elements:
myInts[0] = 100; // Assigns 100 to the first element
int x = myValues[2]; // x will be 6 (the third element)

Serial.println(message[1]); // Prints 'e'

// Iterating through an array:
for (int i = 0; i < 5; i++) {
  Serial.println(myValues[i]);
}

// Multi-dimensional arrays (less common for simple Arduino projects but possible):
int matrix[2][3] = { // A 2x3 matrix (2 rows, 3 columns)
  {1, 2, 3},
  {4, 5, 6}
};
int val = matrix[1][0]; // val will be 4
```

## String Objects and Manipulation
// While C-style character arrays (char arrays ending with a null terminator '\0') are common,
// Arduino also supports the String object, which provides more flexibility.

String myString = "Hello, Arduino!";
String anotherString = String("Another way");

// Concatenation
String combined = myString + " " + anotherString;
Serial.println(combined);

// Getting length
Serial.print("Length of myString: ");
Serial.println(myString.length());

// Comparing strings
if (myString == "Hello, Arduino!") {
  Serial.println("Strings are equal.");
}

// Changing case
myString.toUpperCase();
Serial.println(myString); // Prints "HELLO, ARDUINO!"

// Substring
String sub = myString.substring(7, 14); // Extracts "ARDUINO"
Serial.println(sub);

// Other useful methods:
// startsWith(), endsWith(), indexOf(), lastIndexOf(), replace(), toInt(), toFloat()

// Note: Using String objects extensively can lead to memory fragmentation on smaller Arduinos.
// For simple text manipulation, char arrays are often more memory-efficient.

## Serial Communication
// Used for communication between the Arduino board and a computer or other devices.

```cpp
void setup(){
  // Initialize serial communication at a specified baud rate (bits per second)
  Serial.begin(9600); // 9600 is a common baud rate
}

void loop(){
  // Printing data to the Serial Monitor:
  Serial.print("Hello, ");          // Prints data without a new line
  Serial.println("World!");        // Prints data followed by a new line

  int sensorValue = analogRead(A0);
  Serial.print("Sensor Value: ");
  Serial.println(sensorValue);

  // Printing with different number formats:
  Serial.println(sensorValue, DEC); // Print as decimal (default)
  Serial.println(sensorValue, HEX); // Print as hexadecimal
  Serial.println(sensorValue, OCT); // Print as octal
  Serial.println(sensorValue, BIN); // Print as binary

  // Reading incoming serial data:
  if (Serial.available() > 0) { // Check if there's data waiting to be read
    char incomingByte = Serial.read(); // Read one byte of incoming data
    Serial.print("I received: ");
    Serial.println(incomingByte);

    // For reading strings or numbers, you might need to read multiple bytes
    // and assemble them. Libraries can help with this.
  }
  delay(1000); // Wait a second
}
```

## Using Libraries
Libraries are collections of code that provide extra functionality for your sketches, making it easier to connect to sensors, displays, modules, etc. Arduino comes with a set of built-in libraries, and you can also install third-party libraries.

**Key built-in libraries include:**
*   `Servo`: For controlling servo motors.
*   `Stepper`: For controlling stepper motors.
*   `SoftwareSerial`: For serial communication on other digital pins.
*   `Wire`: For I2C communication.
*   `SPI`: For SPI communication.

**How to use a library:**
1.  **Include the library:** At the top of your sketch, add `#include <LibraryName.h>`. For example, `#include <Servo.h>`.
2.  **Create an instance (if needed):** Some libraries require you to create an object. For example, `Servo myServo;`
3.  **Use library functions:** Call the functions provided by the library. For example, `myServo.attach(9);` and `myServo.write(90);`.

**Example: Using the Servo Library**
This example shows how to sweep a servo motor connected to pin 9 back and forth.

```cpp
#include <Servo.h> // Include the Servo library

Servo myServo;  // Create a Servo object to control a servo
int pos = 0;    // Variable to store the servo position

void setup() {
  myServo.attach(9);  // Attaches the servo on pin 9 to the servo object
}

void loop() {
  // Sweep from 0 degrees to 180 degrees
  for (pos = 0; pos <= 180; pos += 1) { // Goes from 0 degrees to 180 degrees in steps of 1 degree
    myServo.write(pos);              // Tell servo to go to position in variable 'pos'
    delay(15);                       // Waits 15ms for the servo to reach the position
  }

  // Sweep from 180 degrees back to 0 degrees
  for (pos = 180; pos >= 0; pos -= 1) { // Goes from 180 degrees to 0 degrees
    myServo.write(pos);              // Tell servo to go to position in variable 'pos'
    delay(15);                       // Waits 15ms for the servo to reach the position
  }
}
```

**Finding and Installing Libraries:**
You can find and install libraries using the Arduino IDE's Library Manager:
1.  Go to `Sketch > Include Library > Manage Libraries...`.
2.  Search for the library you want.
3.  Select the version and click "Install".

You can also manually install libraries by downloading them as a ZIP file and adding them via `Sketch > Include Library > Add .ZIP Library...`.

## Basic Project Example: Button-Controlled LED
This project demonstrates how to read a digital input (a push button) and control a digital output (an LED).

**Components needed:**
*   Arduino board
*   LED
*   220 Ohm resistor (or similar, for the LED)
*   Push button
*   10k Ohm resistor (for pull-down with the button, if not using INPUT_PULLUP)
*   Breadboard and jumper wires

**Circuit:**
*   Connect one leg of the LED (longer leg, anode) to digital pin 13 through the 220 Ohm resistor.
*   Connect the other leg of the LED (shorter leg, cathode) to GND.
*   Connect one terminal of the push button to digital pin 2.
*   Connect the other terminal of the push button to 5V.
*   Connect a 10k Ohm resistor from digital pin 2 to GND (this is a pull-down resistor, ensuring the pin reads LOW when the button is not pressed).
    *   Alternatively, you can omit the 10k Ohm resistor and configure pin 2 with `pinMode(buttonPin, INPUT_PULLUP);`. In this case, connect the button from pin 2 to GND, and the logic will be inverted (button press reads LOW). We will use `INPUT_PULLUP` in the code example for simplicity.

**Code (using INPUT_PULLUP):**
This code will turn the LED on when the button is pressed and off when it's released.

```cpp
// Pin definitions
const int buttonPin = 2; // The number of the pushbutton pin
const int ledPin = 13;   // The number of the LED pin

// Variable to store the button state
int buttonState = 0;

void setup() {
  Serial.begin(9600); // Initialize serial communication for debugging (optional)

  // Initialize the LED pin as an output:
  pinMode(ledPin, OUTPUT);

  // Initialize the pushbutton pin as an input with an internal pull-up resistor:
  // This means the pin will be HIGH when the button is not pressed,
  // and LOW when the button is pressed (connected to GND).
  pinMode(buttonPin, INPUT_PULLUP);
}

void loop() {
  // Read the state of the pushbutton value:
  buttonState = digitalRead(buttonPin);
  Serial.println(buttonState); // Print button state to serial monitor for debugging

  // Check if the pushbutton is pressed.
  // If it is, the buttonState is LOW because of the INPUT_PULLUP:
  if (buttonState == LOW) {
    // Turn LED on:
    digitalWrite(ledPin, HIGH);
    Serial.println("Button PRESSED - LED ON");
  } else {
    // Turn LED off:
    digitalWrite(ledPin, LOW);
    // Serial.println("Button RELEASED - LED OFF"); // Optional: print when released
  }
  delay(10); // Small delay to debounce, can be adjusted
}
```

**Explanation:**
*   `const int buttonPin = 2;` and `const int ledPin = 13;`: These lines define constant variables to hold the pin numbers for the button and LED, making the code easier to read and modify.
*   `pinMode(ledPin, OUTPUT);`: Configures the LED pin as an output.
*   `pinMode(buttonPin, INPUT_PULLUP);`: Configures the button pin as an input and enables the internal pull-up resistor. This means the pin will read `HIGH` when the button is not pressed and `LOW` when it is pressed (as the button connects the pin to ground).
*   `buttonState = digitalRead(buttonPin);`: Reads the current state of the button (either `HIGH` or `LOW`).
*   `if (buttonState == LOW)`: Since we are using `INPUT_PULLUP`, a `LOW` state means the button is pressed.
*   `digitalWrite(ledPin, HIGH);`: Turns the LED on.
*   `digitalWrite(ledPin, LOW);`: Turns the LED off.
*   `Serial.begin(9600);` and `Serial.println(buttonState);` are included for optional debugging. You can open the Serial Monitor in the Arduino IDE to see the button state.

This project combines digital input, digital output, and the use of an internal pull-up resistor, which are fundamental concepts in Arduino programming.
