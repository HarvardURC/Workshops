# Coding and Electronics workshop

This workshop is intended to guide you through some basic coding techniques, teach you the basics of designing electric circuits as well as give you an introduction to programming an arduino board. If at any point you have a question, don't hesitate to ask one of the HURC members for guidance.

## Getting started:

Installing the Arduino IDE
The first step that needs to be completed before any coding can be done is to set up the correct environment. Since we will primarily be using Arduino boards to program our robots, it is ideal for us to develop in the Arduino IDE. IDE is short for Integrated Development Environment, which contains not only the text editor we need to write our code in, but also a compiler to build our code, and communication protocols with the chip that we are programming. Arduino boards are small boards that contain a microcontroller and easy to use interfaces for programming the processor and using it to control electronics. Follow the steps below to get the Arduino IDE installed:

1. Click [here](http://arduino.cc/en/Main/Software) to access the download page.

2. Download your appropriate installer, depending on what operating system your machine has.

4. Run the installer, and leave all options in their default states. Note: On Windows, you will get a pop up asking to install the Arduino USB Driver. This is very important, so click allow.

5. Once the install finishes, close the installer, and you should have the Arduino IDE installed on your computer!

## The Basics

Now that you have your computer ready, it's time to brush up on the basics. We will first look at electronics and then coding.

### Electronics

First lets dive in to the world of electrical circuits. If you already feel very confident in any of the material that is covered, feel free to skim or skip it.

#### Components

The first thing you need to know before getting started are the components most used in electronic circuits, and how they work (at a very high level). The following are the components that you will need to know in order to begin building simple circuits (and, subsequently, simple robots). Figure 0.1 shows how a component is represented in a circuit schematic, and directly below are pictorial representations.

1. Power sources - A power source provides the voltage ( Volts) and current (Amperes) necessary to drive a circuit. At its core, it is a source of electric potential, and without it a circuit would be useless. Power sources can take the form of batteries, power supplies, or microcontrollers (an Arduino has a max pin output of 5V ). For simplicity, we will be using a DC power source.
2. Resistors - Resistors (Ohms), to put it simply, resist. They impede the flow of electrons through a circuit, and subsequently results in a voltage drop. A voltage drop is a change in the amount of voltage in the circuit, and through it one is able to control how a circuit behaves fairly accurately. One thing to know is that current always follows through the path of least resistance, thus if a current has a choice between a 500 Ohm resistor and a 10000 ohm resistor, it will flow through the 500 ohm resistor.
3. Potentiometers (aka pots) - Potentiometers are essential variable resistors. While a resistor can only have a fixed resistance, potentiometers can be tuned to any resistance within its range (we will be using 10 kOhm pots, meaning they can take a value between 0 Ohms and 10000 Ohms).
4. LEDs - LED stands for Light Emitting Diode. In its simplest form, it turns current into light and heat, while at the same time acting like a resistor and producing a voltage drop. Because LEDs are diodes, it is important to know that they only work if connected in the proper direction (the longer leg is the positive end, the shorter leg is the negative end).
5. Capacitors - Capacitors act like buckets for electricity; they store charge and can thus be used as temporary and small batteries (as well as producing some other useful phenomenon). Capacitors, like LEDs, are polarized and will only work if placed in circuit in the correct orientation.

![Components](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.1.jpg)  
Figure 0.1: The components we’ll be working with

#### Breadboarding

The next important step is learning the layout of the breadboard. A breadboard is a tool made for the quick prototyping of circuits. It is easy to build circuits, and fix mistakes because components and wires are stuck into the sockets of a breadboard rather than being soldered together permanently. Figure 0.2 shows the layout of an example breadboard. From the image you can see that if a breadboard is held vertically, the rows in the middle are connected together and essentially act as a single point. Similarly, the columns to the left and right of the breadboard are connected together. The rows are where you will be connecting most of your components and the columns are usually used for power and ground.

![A breadboard](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.2.jpg)  
Figure 0.2: A standard breadboard

In this section, we will review the basic building blocks of an Arduino sketch (the common name of an Arduino program), and work through several examples that will highlight these ideas. Our main reference for this section will be the official Arduino reference, which can be found [here](http://arduino.cc/en/Reference/HomePage). It is probably a lot to take in at once, but this page will probably answer any questions you might have about the syntax of the arduino language.

#### Ohm's Law

Ohm's Law is as follows: V = I * R, where V is voltage, I is current and R is resistance. In other words, The voltage drop across 2 points is proportional to the current flowing between those points and the resistance between the points. This formula (perhaps the most important in all of electronics) is extremely useful for most simple circuits, and for all the circuits being built today. The linear relation between V and I or V and R means that if we know any of the two values of a circuit, we can calculate all parameters that define how it works. We also have the power equation: P = V * I = I^2*R = V^2 / R, where P is power. The power value in an LED will determine how bright it shines and in a resistor, how much heat it will dissipate.

#### Circuits in Series and Parallel

Looking at the schematic in Figure 0.3 you can see that the LED and resistor are in series in the circuit diagram. As you can see on the breadboard to the right, components in series need to share at least one row. The row allows for one component to conduct to another.

![A circuit in series](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.3.png)  
Figure 0.3: An LED and resistor in series

Looking at the schematic in Figure 0.4 you can see that the resistor and capacitor are in parallel in the circuit diagram. As you can see on the breadboard on the right, components in parallel need to share both rows as points of contact. When components share rows in this way, current must flow into both of them at the same time, this making the connection a parallel one.

![A circuit in parallel](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.4.png)  
Figure 0.4: A capacitor and resistor in parallel

##### Exercises

1. Build the circuit in Figure 0.3 and watch the LED come to life. Break the circuit and add another resistor in series (you should now have an LED in series with a resistor in series with another resistor). What happened to the brightness of the LED?

2. Kirchhoff's current law may be just as important as Ohms law in circuit analysis. It basically means that the amount of current entering a junction is equal to the current exiting the junction. That is Σ I = 0. In simpler terms, this law says that the amount of current entering a set of parallel components does not have to be equal; current splits. Voltage on the other hand is the same. Thus, the power that a certain component gets is affected by whether or not it is in series with something else. Build the circuit in Figure 0.5. Now what happened to the brightness of the LED?

![An LED in parallel with 2 resistors in series](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.5.png)  
Figure 0.5: An LED in parallel with 2 resistors in series

3. Now rebuild your circuit, so that it looks like the one in figure 0.6. What happened to the brightness of the LED? Why?

![An LED and 2 resistors in parallel](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.6.png)  
Figure 0.6: An LED and 2 resistors in parallel

#### Measuring resistance, voltage and current

A multimeter is used to measure the V, I, and R -values at certain points in a circuit. Instead of using multiple separate devices, you can simply turn the dial on a multimeter to turn it into a voltmeter, ammeter or some other measurement device. The way multimeters measure voltage, current, and resistance are fundamentally different. A voltmeter must be placed in parallel to what you want to measure in order to find the voltage. An ammeter on the other hand must be placed in series with the circuit; the best way to do so is to pretend that it is another resistor. In Figure 0.7 you can see how a voltmeter and ammeter are placed properly in order to measure voltage or current. In order to measure the resistance of an element, you have to connect the multimeter in parallel to the component, Similarly to how you would measure voltage.

![How to properly connect a voltmeter and ammeter](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.7.png)  
Figure 0.7: How to properly connect a voltmeter and ammeter

##### Exercises

1. Build the circuit from Figure 0.3. First measure the voltage of the power source by placing the probes in the buses of the breadboard (if the probe doesn't fit in to the holes, use a piece of wire to make the connection). Next, measure the voltage across the LED by placing the voltmeter in parallel with it. Next measure the voltage across the resistor. What do you notice about the voltage drops?

2. Now measure the current in the circuit at various places (before the LED, between the LED and the resistor, and after the resistor). What do you notice about the current?

3. Now rebuild the circuit from Figure 0.6 and make similar measurements. What do you notice? Can you explain what you see?

Hopefully by now you have realized the difference between components in parallel and components in series. When in series, V will change at every interval, but current will stay the same. When in parallel, V will stay constant throughout, but current will change depending on what branch of the parallel tree you are measuring.

#### Voltage Divider

An important consequence of the voltage drop is that it can be used to control a circuit precisely and towards our needs. The so-called voltage divider circuit uses this phenomenon to create an output voltage of our choosing. See Figure 0.8 for an example of a generic voltage divider circuit.

![A standard voltage divider](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.8.jpg)  
Figure 0.8: A standard voltage divider

##### Exercises

1. First, build the voltage divider circuit, where R1 = R2. Measure the voltage drop across resistor AB. What is the relation between this drop and the output voltage of our power source? Place an LED in parallel with R2.

2. Now replace R1 with a resistor at least 10 times the value of R2. What is the voltage drop across AB now? What happens to the LED?

3. Now return R1 to its original value and replace R2 with a value 100 times bigger than R1. What is the voltage drop across AB?

As you have probably guessed by now, there is a linear relationship between the input voltage and output voltage, where the resistance are the slope. From our observations of the output voltage and the LED, we can see that when R2 » R1, the output voltage is highest, and when R1 » R2 the output voltage is lowest. The formula for a voltage divider circuit is the following: Vout = Vin * R2/(R1+R2).

### Coding

Now that you know the basics of designing an electric circuit, it's time to learn basic arduino coding. Once again, if you already feel comfortable with any of the material covered, feel free to skip it.

First thing you have to do is familiarize yourself with the arduino board. Please review [this tutorial](http://arduino.cc/en/Guide/Board?from=Tutorial) for a general overlay of the Arduino Uno board. Although we may not be using the Uno for our actual projects, understanding the Uno board is key to understanding other Arduino boards. Don't worry if you don't understand everything just yet.

Once you've familiarized yourself with the arduino board, open up the arduino IDE that you installed previously.

#### The Arduino sketch

Every Arduino sketch has two main components, a setup and a loop function, as seen below:

The setup function runs once when you press reset or power the board:
```ino
void setup () {
  // code here
}
```
The loop function runs over and over again indefinitely:
```ino
void loop () {
  //code here
}
```

As seen in the comments, the setup function of the Arduino function only runs once, and before any other code is run. The main purpose of this section is to initialize any global variables that might be used later, set up board pins for use (which board pin controls what), etc. The loop function is the main logic function of the Arduino sketch. It does exactly what you would expect it to - it loops! Generally, all the logic of the Arduino sketch is contained in this function.

#### Blink

Let’s quickly examine pins and writes in action. Head [here](http://www.arduino.cc/en/Tutorial/Blink) and follow the tutorial there. You can find the code already written in your Arduino IDE by going to File>Examples>01.Basics>blink. The next segment will teach you how to load the sketch onto the actual Arduino board.

#### Uploading code

To upload a Arduino sketch from the IDE to the board, simply follow these steps once you have an arduino sketch open:

1. Compile your Arduino sketch using the check mark button in the top toolbar. This will build your sketch code, and check if there are any syntactical issues. If there are, you should fix them now.

2. Connect the micro-USB end of the USB wire into the board, and the USB end into your computer. If you completed the driver steps, your board should be recognized with no issues.

3. Go to Tools>Board and make sure you have the correct board specified. For this tutorial we are using either the Arduino Uno or Micro. If you're not sure which board you have, ask one of the HURC members.

4. Go to Tools>Serial Port, and make sure you have the correct board for your board selected. There generally is only one port, but if there are more, trial and error usually works.

5. Click on the Right Arrow button in the toolbar to upload your code.

#### Syntax

The Arduino IDE uses a custom programming syntax known as INO, which is really just a derivative of C/C++. Because of that, the syntax in Arduino sketches is almost exactly the same is in C or C++ programs. The full supported syntax is listed out in the [Arduino reference](https://www.arduino.cc/en/Reference/HomePage). Make sure you are comfortable with the structure section.

For coding projects in any language, but Ino in specific you have to be able to use:  

1. if and if ... else statements  

2. for and while loops  

3. arithmetic operations  

4. comparison operations  

5. boolean operations  

6. constants and variables  

7. boolean, char, int, string and array data types  

8. [Serial Print](https://www.arduino.cc/en/Serial/Print)  

This is a lot to go through right now. If you have any prior experience with coding, then most of this should simply be looking up the new syntax. If you aren't familiar with theses concepts, then don't try to go through all of the reference right now. Instead focus on the aspects that you think will help you solve a particular exercise as you go through this workshop.

##### Exercise 1.1 (Serial Print, strings)
Write an Arduino sketch to print "Hello World!". Make sure to use correct Arduino sketch layout.

##### Exercise 1.2 (for loops, variables)
Build on the following Arduino sketch so that it prints a 10-level left-aligned pyramid of asterisks. Make sure you use the variable levels in your loop function.

```ino
void setup () {
  int levels = 10;
}

void loop () {
  Serial.print("#");
}
```

Expected output:

\#  
\#\#  
\#\#\#  
\#\#\#\#  
\#\#\#\#\#  
\#\#\#\#\#\#  
\#\#\#\#\#\#\#  
\#\#\#\#\#\#\#\#  
\#\#\#\#\#\#\#\#\#  
\#\#\#\#\#\#\#\#\#\#  

##### Exercise 1.3 (arrays)

Write an Arduino sketch that creates the following array {0, 1, 2, 3, 4, 5, 6, 7, 8, 9} using a while loop.

#### Functions

Functions are the building blocks for more advanced logic. Instead of writing all logic inside the central loop function, we can create functions to separate out logic, and simply call those functions within the loop. Not only does this help us keep track of the specific purpose of parts of our code, but it also helps us keep our code clean and manageable.

Writing functions in an Arduino sketch is identical to writing a function in any C program. Simply define the output type, the name of the function, and any inputs into the function.

```ino
int functionName  (int input1, char input2) {
  // . . .  logic here . . .
}
```

In the snippet above, we have a function called functionName with output type integer, and two inputs: an integer input1, and a char input2. As an aside, if you are familiar with C systems programming, you are probably used to dynamic memory allocation using the malloc() and free() commands, and returning allocated addresses. Arduino boards don’t have a heap, so you won’t be able to take advantage of that here. All logic should be done at the stack and global level.

##### Exercise 2.1

Write a function that takes in two integers as input, and returns the integer sum of them.

##### Exercise 2.2

Write a function that, when given a integer n, produces an array of with the first n Fibonacci numbers in it.

##### Exercise 2.3 (Optional)

Call the first function in the second function so that after the Fibonacci array is created, the sum off all elements in the array is computed.

##### Coding challenge

Write a function that takes a list of strings an prints them, one per line, in a rectangular frame. For example the list ["Hello", "World", "in", "a", "frame"] gets printed as:

\*\*\*\*\*\*\*\*\*  
\* Hello__ \*  
\* World__\*  
\* in_____ \*  
\* a______\*  
\* frame__ \*  
\*\*\*\*\*\*\*\*\*  

NOTE: Underscores represent spaces.
Use a separate function for determining the frame width that takes in the list of words as an input and a separate function for printing a line of the frame, that takes in a word and the frame width.

## Final Challenge

For this final challenge you will merge the skills you've just learnt. But first you have to learn how to interface with the Arduino microcontroller. A Microcontroller both accepts and outputs current. There are designated pins in the Arduino which accept analog inputs or digital inputs (we will not delve into the details behind the differences). These inputs can then, with a little code, be used to control the output of the Arduino in such a way that we can output the right out amount of voltage to a target location (via a specific output pin). In this next exercise you will explore the magic of analog-digital interfacing. Such interfacing is essential in robotics, because most times robots need to be autonomous or controlled remotely, and a microcontroller like an Arduino can be programmed to control the circuitry in the way that we want it.

Read the following to know how to read from and write to an Arduino pin:

1. [PinMode](https://www.arduino.cc/en/Reference/PinMode)

2. [DigitalRead](https://www.arduino.cc/en/Reference/DigitalRead)

3. [DigitalWrite](https://www.arduino.cc/en/Reference/DigitalWrite)

For this challenge you should find one or two more participants to pair up with. You will be building a 3-bit binary counter. You will need the following components:

1. 1 Microcontroller

2. 3 LEDs

3. 2 pushbuttons

4. Some resistors

The counter should use the 3 LED's to display the numbers 0 to 7 in binary (000, 001, 010, 011, 100, 101, 110, 111) and the 2 pushbuttons to either increment and decrement the count. You should code to protect against over and underflow (if the user tries to count to higher than 7 or lower than 0, the count should not change).

This challenge might prove to be quite difficult if you don't have a lot of electronics or coding experience. Don't hesitate to ask a HURC member for help. We're here to mentor you.
