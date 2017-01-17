# HURC Wintersession Workshop: Robot Rover

Welcome to the Harvard Undergraduate Robotics Club's Wintersession workshops! Over the course of these workshops, you will be constructing a miniature robot rover from the ground up. [ADD SOME STUFF HERE!!!]. If at any point you have a question, don't hesitate to ask one of the HURC members for guidance.

## Part One: Mechanical Design
### Getting Started

### What if I'm a Solidworks Noob?
That's fine! If you haven't used SolidWorks before, follow the steps below to complete an example project to gain some familiarity. If you are comfortable with Solidworks, skip to the next section.

1. Open SolidWorks by clicking on the appropriate icon on the desktop.

2. In the top left corner, start a new part by clicking "File -> New" or by clicking the white page icon in the top toolbar.

3. When prompted, select "New Part."

4. In the bottom right corner of the window, there should be a bar that says either "IPS" (Inch/Pound/Second) or "MMGS" (Millimeter/Gram/Second). Click on this bar and select "IPS". HURC will work almost exclusively in inches.

5. Now you are ready to begin constructing your part. In the top right corner, underneath the top toolbar, click "Extruded Boss/Base." The symbol for this is a yellow square with a smaller green square overlaid.

6. The window will prompt you to choose one of three planes to construct your part in: Top, Front, or Right. Select the "Front" plane.

7. We will be designing a door-stop that consists of two parts. This might seem to be a device that should just be one part. That's because it is, but this is a tutorial so just humor us.

8. You should now be in the "Edit Sketch" mode. Begin by drawing a line (select the "Line" tool from the toolbar on the top of the page) from the origin horizontally to the right. Do not worry about the length of this line at the moment.

9. Draw a second line also from the origin, extending at an arbitrary angle to the top right. Do not worry about the length of this line or the angle between the two lines.

10. Draw a third line connecting the two lines you have drawn previously. You should now have a triangle with one horizontal side pictured on your screen.

11. Deselect the "Line" tool. Do NOT click "Exit Sketch"

12. Click on the third line that you drew. On the left side of the screen, there should be the option to "Add Relation". Click on "vertical." You should now have a right triangle on your screen.

13. Hold down the right-click button on your mouse, move your mouse upward, then release the right-click button. You should now be in the "Smart Dimension" mode.

14. Click on the horizontal line. It will prompt you to input the desired length - input "2 in" or simply "2". Hit enter.

15. Click on the angled line. It will prompt you to input the desired length. Do NOT input a length; instead, click again on the horizontal line. This will allow you to define the angle between the lines. Set the angle to 20 degrees.

16. Click on "Exit Sketch" at the top left. You will be prompted to define the extrusion measurement (the depth of the 3D part). Set it to be "3/4 in" or simply "3/4". Or if it floats your boat "0.75". Hit enter.

17. You should now see a 3D wedge on your screen. You can manipulate your view of the wedge by pushing the mouse's scroll wheel in and moving the mouse or by hitting Ctrl + n, where n is any number between 1 and 8.

18. We are almost done with this part. Hit Ctrl + 4 or otherwise navigate to view the vertical end of the part.

19. On the top toolbar, click on "Hole Wizard." It will prompt you to choose a face on which to construct the hole. Select the vertical end currently in your view.

20. On the left-hand side, select "Straight tap" and set the thread sizes to be ANSI-inch. Then, select the option of "10-32".

21. Set the depth of the hole to be 0.5"

22. Click on the "Positions" tab. Click once anywhere on the selected face.

23. Use "Smart Dimension" (recall from earlier) to set the point to be 0.25" from the bottom of the stop, and 0.5" from the right.

24. You are done with this part! Create a new folder called "HURC tutorial_YOUR NAME" on the Desktop and save the part in that folder with the file name of "Door stop 1"

### Building your Robot Chassis

## Part Two: Circuits and Coding
### Getting Started
Once we have assembled the components of the robot, we need to connect them in a circuit that is controlled by a microcontroller, which is basically a computer without the operating system. For this project, you will be using an Arduino Uno programmed in the Arduino Programming Language (documentation [here](https://www.arduino.cc/en/Reference/HomePage)), which is essentially C/C++, but with some minor variations to tailor it for microcontrollers. 

In order to upload programs to the microcontroller, you need to install the Arduino IDE. IDE is short for Integrated Development Environment, which contains not only the text editor we need to write our code in, but also a compiler to build our code, and communication protocols with the chip that we are programming. Arduino boards are small boards that contain a microcontroller and easy to use interfaces for programming the processor and using it to control electronics. Follow the steps below to get the Arduino IDE installed:

1. Click [here](http://arduino.cc/en/Main/Software) to access the download page.

2. Download your appropriate installer, depending on what operating system your machine has.

4. Run the installer, and leave all options in their default states. Note: On Windows, you will get a pop up asking to install the Arduino USB Driver. This is very important, so click allow.

5. Once the install finishes, close the installer, and you should have the Arduino IDE installed on your computer!

### A Brief Introduction to Circuits

Before you begin messing about with the Arduino, it is good to have an understanding of circuit theory.

#### Components

The first thing you need to know before getting started are the components most used in electronic circuits, and how they work (at a very high level). The following are the components that you will need to know in order to begin building simple circuits (and, subsequently, simple robots). Figure 0.1 shows how a component is represented in a circuit schematic, and directly below are pictorial representations.

1. Power sources - A power source provides the voltage (Volts) and current (Amperes) necessary to drive a circuit. At its core, it is a source of electric potential, and without it a circuit would be useless. Power sources can take the form of batteries, power supplies, or microcontrollers (an Arduino has pins for 3.3V and 5V out). 
2. Resistors - Resistors (Ohms), to put it simply, resist. They impede the flow of electrons through a circuit, and subsequently results in a voltage drop. A voltage drop is a change in the amount of voltage in the circuit, and through it one is able to control how a circuit behaves fairly accurately. One thing to know is that current always follows through the path of least resistance, thus if a current has a choice between a 500 Ohm resistor and a 10000 ohm resistor, it will flow through the 500 ohm resistor.
3. Potentiometers (aka pots) - Potentiometers are essentially variable resistors. While a resistor can only have a fixed resistance, potentiometers can be tuned to any resistance within its range.
4. LEDs - LED stands for Light Emitting Diode. In its ideal form, it turns current into light, while at the same time producing a voltage drop. Because LEDs are diodes, it is important to know that they only work if connected in the proper direction (the longer leg is the positive end, the shorter leg is the negative end).
5. Capacitors - Capacitors act like buckets for electricity; they store charge and can thus be used as temporary and small batteries (as well as producing some other useful phenomenon). Some capacitors, like LEDs, are polarized and will only work if placed in circuit in the correct orientation (these will be clearly marked). **Please make sure a polarized capacitor is plugged in correctly. They will explode if the polarization is reversed!**

![Components](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.1.jpg)  
Figure 0.1: The components we’ll be working with

#### Breadboarding

The next important step is learning the layout of the breadboard. A breadboard is a tool made for the quick prototyping of circuits. It is easy to build circuits, and fix mistakes because components and wires are stuck into the sockets of a breadboard rather than being soldered together permanently. Figure 0.2 shows the layout of an example breadboard. From the image you can see that if a breadboard is held vertically, the rows in the middle are connected together and essentially act as a single point. Similarly, the columns to the left and right of the breadboard are connected together. The rows are where you will be connecting most of your components and the columns are usually used for power and ground.

![A breadboard](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.2.jpg)  
Figure 0.2: A standard breadboard

In this section, we will review the basic building blocks of an Arduino sketch (the common name of an Arduino program), and work through several examples that will highlight these ideas. Our main reference for this section will be the official Arduino reference, which can be found [here](http://arduino.cc/en/Reference/HomePage). It is probably a lot to take in at once, but this page will probably answer any questions you might have about the syntax of the arduino language.

#### Ohm's Law

Ohm's Law is as follows: V = I * R, where V is voltage, I is current and R is resistance. In other words, The voltage drop across 2 points is proportional to the current flowing between those points and the resistance between the points. This formula (perhaps the most important in all of electronics) is extremely useful for most simple circuits, and for all the circuits being built today. The linear relation between V and I or V and R means that if we know any of the two values of a circuit, we can calculate all parameters that define how it works. We also have the power equation: P = V * I = I^2*R = V^2 / R, where P is power. The power value in an LED will determine how bright it shines and in a resistor, how much heat it will dissipate.

#### Circuits in Series and Parallel

Looking at the schematic in Figure 0.3 you can see that the LED and resistor are in series in the circuit diagram. As you can see on the breadboard to the right, components in series need to share at least one row. The row allows for one component to conduct to another.

![A circuit in series](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.3.png)  
Figure 0.3: An LED and resistor in series

Looking at the schematic in Figure 0.4 you can see that the resistor and capacitor are in parallel in the circuit diagram. As you can see on the breadboard on the right, components in parallel need to share both rows as points of contact. When components share rows in this way, current must flow into both of them at the same time, this making the connection a parallel one.

![A circuit in parallel](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.4.png)  
Figure 0.4: A capacitor and resistor in parallel

#### Measuring resistance, voltage and current

A multimeter is used to measure the V, I, and R -values at certain points in a circuit. Instead of using multiple separate devices, you can simply turn the dial on a multimeter to turn it into a voltmeter, ammeter or some other measurement device. The way multimeters measure voltage, current, and resistance are fundamentally different. A voltmeter must be placed in parallel to what you want to measure in order to find the voltage. An ammeter on the other hand must be placed in series with the circuit; the best way to do so is to pretend that it is another resistor. In Figure 0.7 you can see how a voltmeter and ammeter are placed properly in order to measure voltage or current. In order to measure the resistance of an element, you have to connect the multimeter in parallel to the component, similarly to how you would measure voltage.

![How to properly connect a voltmeter and ammeter](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.7.png)  
Figure 0.7: How to properly connect a voltmeter and ammeter

#### Voltage Divider

An important consequence of the voltage drop is that it can be used to control a circuit precisely. The so-called voltage divider circuit uses this phenomenon to create an output voltage of our choosing. See Figure 0.8 for an example of a generic voltage divider circuit.

![A standard voltage divider](https://raw.githubusercontent.com/HarvardURC/Workshops/master/assets/coding_electronics/fig%200.8.jpg)  
Figure 0.8: A standard voltage divider

### A Briefer Introduction to Servo Motors

### Working with the Arduino Microcontroller

The first thing you should probably do is review [this tutorial](http://arduino.cc/en/Guide/Board?from=Tutorial) for a general overlay of the Arduino Uno board. Don't worry if you don't understand everything just yet.

As mentioned before, the Arduino language is really just a derivative of C/C++. Because of that, the syntax in Arduino sketches is almost exactly the same is in C or C++ programs. The full supported syntax is listed out in the [Arduino reference](https://www.arduino.cc/en/Reference/HomePage). Make sure you are comfortable with the structure section.

For coding projects in any language, but Arduino specifically you have to be able to use:  

1. if and if ... else statements  

2. for and while loops  

3. arithmetic operations  

4. comparison operations  

5. boolean operations  

6. constants and variables  

7. boolean, char, int, string and array data types  

8. [Serial Print](https://www.arduino.cc/en/Serial/Print)  

This is a lot to go through right now. If you have any prior experience with coding, then most of this should simply be looking up the new syntax. If you aren't familiar with these concepts, then don't try to go through all of the reference right now. Instead focus on the aspects that you think will help you solve a particular exercise as you go through this workshop.

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

Let’s quickly examine pins and writes in action. Head [here](http://www.arduino.cc/en/Tutorial/Blink) and follow the tutorial there. You can find the code already written in your Arduino IDE by going to File>Examples>01.Basics>blink. The next segment will teach you how to load the sketch onto the Arduino board.

#### Uploading code

To upload a Arduino sketch from the IDE to the board, simply follow these steps once you have an arduino sketch open:

1. Compile your Arduino sketch using the check mark button in the top toolbar. This will build your sketch code, and check if there are any syntactical issues. If there are, you should fix them now.

2. Connect the USB Type-B end of the USB wire into the board, and the USB Type-A end into your computer. If you completed the driver steps, your board should be recognized with no issues.

3. Go to Tools>Board and make sure you have the correct board specified. For this tutorial we are using the Arduino Uno.

4. Go to Tools>Serial Port, and make sure you have the correct board for your board selected. There generally is only one port, but if there are more, trial and error usually works.

5. Click on the Right Arrow button in the toolbar to verify and upload your code.

##### Exercise 1.1 (Serial Print, strings)
Write an Arduino sketch to print "Hello World!". Make sure to use correct Arduino sketch layout. **This will be useful for debugging, as you can insert print statements in your code to check execution.**

##### Exercise 1.2 (for loops, variables)
Build on the following Arduino sketch so that it prints a 10-level left-aligned pyramid of asterisks. Make sure you use the variable levels in your loop function.

```ino
void setup () {
  int levels = 10;
  Serial.begin(9600);
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

As a final note, here are some links to documentation you may find helpful for configuring and using the pins of the Arduino:

1. [PinMode](https://www.arduino.cc/en/Reference/PinMode)

2. [DigitalRead](https://www.arduino.cc/en/Reference/DigitalRead)

3. [DigitalWrite](https://www.arduino.cc/en/Reference/DigitalWrite)

4. [AnalogRead](https://www.arduino.cc/en/Reference/AnalogRead)

For your reference, we have included a pinout diagram for the Arduino Uno.
![Pinout Diagram for the Arduino Uno R3](https://raw.githubusercontent.com/HarvardURC/Workshops/master/Wintersession/assets/uno_pinout.jpg)

### Your Circuit Doesn't Work! A Quick Note on Debugging.

### Connecting Everything Together

#### Battery Power

### Bonus!
Having a robot rover that moves around according to your commands is pretty cool, but it would be way better if it could respond to its environment. If you have extra time, add a sensor to your robot! We will supply an assortment of sensors which you can attach to your robot to gain feedback from the environment. All of these can be connected to the Arduino for both power and communications.
