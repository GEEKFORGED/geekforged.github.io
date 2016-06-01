---
layout: post
title:  "Hello Arduino"
date:   2016-05-19 21:47:23 -0400
categories: Arduino
tags: tutorial
---

So, you finally went out and got yourself an Arduino. I believe congratulations are in order. Now, if you don't have one; go get one so I can congratulate you.

In this project, we will start out by simply making an LED blink. Even if you have no idea what an LED is, that's okay we will go over that too! Now, there is a little bit of setup required on your computer before we can start. If you have previously uploaded a program to your Arduino with your computer and are comfortable with doing it again, go ahead and [skip to the project](#project).

## Setup

### What you will need:
* Arduino (of course!)
* USB A-B cable
* Computer or Laptop

### Getting the software
Go to the [Arduino.cc][arduino_cc] site and navigate to the download page. You should see the latest stable version of their software near or at the top of the page. Select your operating system of preference. Feel free to throw them a donation. If you don't want to, they understand, click the "just download" button.

### Installing the software
Assuming that your download was successful go ahead and install the software. Note: if you have any issues installing the software, checkout their official [getting started guide][arduino_cc_getting_started] and select your operating system. If you can't find solace there, hit up Google; it's never failed me yet. Besides if you are experiencing an issue, when it comes to Arduino, chances are someone else already ran into it and found a solution.

### Setting up your environment
Go ahead and open up the Arduino application if it is not already open. In the tool-bar at the top, you will see a "Tools" menu. Click it, then in the sub-menu that opens up click "Board". Select your board from that menu. The board I have is an Uno, so I selected "Arduino/Genuino Uno". Now, make sure that your Arduino board is not plugged into your computer via the USB cable. If it is, unplug it. Below the "Board" menu, there should be a "Port" menu. Take note of its contents. Now go ahead and plug in your Arduino. Your Arduino should be the entry that has changed in the "Port" menu; select it.

At this point, you have told your computer what type of board you are using, and how to talk to it. You can now begin uploading code to your Arduino to control your circuits!

---

## Project

### What you will need:
* Arduino (of course!)
* USB A-B cable
* Computer or Laptop
* Breadboard
* Jumper wire x 4
* LED x 1
* Resistor 220&#8486; x 1 (*Note that any resistor above 220&#8486; up to 1K&#8486; should work.*)

### Understanding circuit diagrams
In these projects, you will find two different types of diagrams. The first will be a breadboard view, as if you were plugging the components directly into your own breadboard. The second is a schematic view of the circuit. It is up to you, which one you wish to follow along with; in fact both formats might be helpful once we get into more complex circuits!

### Setting up the circuit
To begin, set your Arduino next to the breadboard; leaving the Arduino powered off for the moment. Jump the ground pin of the Arduino to the blue, or negative power rail on the breadboard. Next, jump pin 13 to the positive, or red power rail on the breadboard. If your not quite sure how to get around your breadboard yet, that's okay. Simply reference the provided images as a guide. {::comment}Checkout our [primer on breadboards][breadboard_primer].{:/comment}

The next step is to take your 220&#8486; resistor and plug it into the breadboard. Proceed by jumping from the positive power rail to the resistor. Then plug the Anode side of the LED (that's the side with the longer leg) {::comment}[Anode side of the LED][led_primer]{:/comment} into the row containing the other end of the resistor. The final step is to jump from the Cathode side of the LED (the "flat tire side" also with the shorter leg){::comment}[Cathode side of the LED][led_primer]{:/comment} to the negative power rail on the breadboard.

![Arduino blink circuit - breadboard]({{site.baseurl}}/assets/images/Arduino_blink_circuit_bb.svg){:width="50%" height="50%"}

### There are many ways to slice a cake
Theoretically, you may lay your circuit out however you wish on your breadboard (As long as the layout of the circuit does not change). By doing so, you can even save the use of two wires. Here is the circuit diagram, feel free to play with the circuit and lay it out as you wish! *Don't be afraid of circuit diagrams, they can be extremely helpful.* The circuit diagram is simply an abstraction of the breadboard diagram. It's just a matter of learning the symbols, which are conveniently labeled.

![Arduino blink circuit - schematic]({{site.baseurl}}/assets/images/Arduino_blink_circuit_schem.svg){:width="50%" height="50%"}

### Making the circuit do something
If your Arduino is brand new, and you have never done any projects with it, there is a good chance that it has the factory blink application on it. In that case your LED will already be blinking. The problem with factory code is that it just isn't as much fun as the stuff that we can come up with ourselves... Besides, we can't bend it to our will or forge an evil army of robot Arduinos, running the stock code. Whether the LED blinks or not at the moment, lets make it do what we want it to do.

Assuming that you have followed the instructions to this point, plug your Arduino into your computer, and open the Arduino software. It turns out that the Arduino software comes pre-packaged with some example programs that you can upload to your Arduino to play around with. One of these such example programs is called "Blink".

In the Arduino software, click File > Examples > Basics > Blink. This will open the "Blink" example file, and it should look like this:

~~~ cpp
/*
  Blink
  Turns on an LED on for one second, then off for one second, repeatedly.

  Most Arduinos have an on-board LED you can control. On the Uno and
  Leonardo, it is attached to digital pin 13. If you're unsure what
  pin the on-board LED is connected to on your Arduino model, check
  the documentation at http://www.arduino.cc

  This example code is in the public domain.

  modified 8 May 2014
  by Scott Fitzgerald
 */


// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin 13 as an output.
  pinMode(13, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(13, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);              // wait for a second
  digitalWrite(13, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);              // wait for a second
}
~~~

Before uploading any code to the Arduino, it is always handy to *verify* it first. To do so, click the "Check-mark" button at the top of the screen. If everything went well, you should see a "Done Compiling" message in the green bar above the black output pane. If something did go wrong, the green bar would turn red and contain the error message. At this point however, since we haven't changed any of the code, everything should be fine.

Now it's time to upload our code to the Arduino! Make sure that your USB cable is plugged into the Arduino. Go ahead and click the "Right arrow" button located next to the verify button (don't ask me why it is a right arrow... it's not even close to conventional for upload...). You might see the lights on your Arduino act a bit sporadic for a few seconds. This is completely normal as the unit is rebooting with the new code on it (hopefully). Once it stops blinking like crazy, you should see it blink on for one second, then off for the next. It will repeat this process indefinitely for as long as it is powered on.

To demonstrate the first snowflake on the tip of the iceberg that is Arduino, go ahead and play with the timings. Anywhere you see:

~~~ cpp
delay(1000);              // wait for a second
~~~

You can change the number 1000 to be whatever time you want in milliseconds. Remember that 1000ms is equal to 1 second. An example of a simple change you could make would be:

~~~ cpp
digitalWrite(13, HIGH);   // turn the LED on (HIGH is the voltage level)
delay(1000);              // wait for a second
digitalWrite(13, LOW);    // turn the LED off by making the voltage LOW
delay(2000);              // wait for a second
~~~

Go ahead and verify your code, then upload it to your Arduino. You should see that the led will be on for a total of 1 second, and will stay off for a total of two seconds. Try making the numbers smaller, play with them a bit, you may find a sweet spot where the LED appears to be on all the time, but appears to be dim as well. It just happens that there is a name for this "dimming trick" called Pulse Width Modulation, however that is a topic for another time.

[arduino_cc]: http://arduino.cc
[arduino_cc_getting_started]: http://arduino.cc/en/Guide/HomePage
