---
layout: post
title:  "Hello Arduino"
date:   2016-05-19 21:47:23 -0400
categories: Arduino
---

So, your ready for your very first Arduino project. Perfect, just make sure that you have set up your computer properly. If you haven't, now would be a good time to take a look at my post on [setting up your computer][setting_up_your_computer_post].

In this project, we will start out by simply making an LED blink, we will then move on to transform it into a signal lamp, more commonly known as a Morse lamp. Even if you have no idea what an LED is, that's okay we will go over that too!

## What you will need:
* Arduino (of course!)
* USB A-B cable
* Computer or Laptop
* Breadboard
* Jumper wire x 4
* LED x 1
* Resistor 220&#8486; x 1 (*Note that any resistor above 220&#8486; up to 1K&#8486; should work.*)

## Understanding circuit diagrams
In these projects, you will find two different types of diagrams. The first will be a breadboard view, as if you were plugging the components directly into your own breadboard. The second is a schematic view of the circuit. It is up to you, which one you wish to follow along with; in fact both formats might be helpful once we get into more complex circuits!

## Setting up the circuit
To begin, set your Arduino next to the breadboard; leaving the Arduino powered off for the moment. Jump the ground pin of the Arduino to the blue, or negative power rail on the breadboard. Next, jump pin 13 to the positive, or red power rail on the breadboard. If your not quite sure how to get around your breadboard yet, that's okay. Checkout our [primer on breadboards][breadboard_primer].

The next step is to take your 220&#8486; resistor and plug it into the breadboard. Proceed by jumping from the positive power rail to the resistor. Then plug the [Anode side of the LED][led_primer] into the row containing the other end of the resistor. The final step is to jump from the [Cathode side of the LED][led_primer] to the negative power rail on the breadboard.

![Arduino blink circuit - breadboard]({{site.baseurl}}/assets/images/Arduino_blink_circuit_bb.svg){:width="50%" height="50%"}

## There are many ways to slice a cake
Theoretically, you may lay your circuit out however you wish on your breadboard (As long as the layout of the circuit does not change). By doing so, you can even save the use of two wires. Here is the circuit diagram, feel free to play with the circuit and lay it out as you wish! *Don't be afraid of circuit diagrams, they can be extremely helpful.* The circuit diagram is simply an abstraction of the breadboard diagram. It's just a matter of learning the symbols, which are conveniently labeled.

![Arduino blink circuit - schematic]({{site.baseurl}}/assets/images/Arduino_blink_circuit_schem.svg){:width="50%" height="50%"}

## Making the circuit do something
If your Arduino is brand new, and you have never done any projects with it, there is a good chance that it has the factory blink application on it. In that case your LED will already be blinking. Factory code, just isn't as much fun as the stuff that we can come up with ourselves... Besides, we can't bend it to our will or forge an evil army of robot Arduinos running stock code. Whether the LED blinks or not at the moment, lets make it do what we want it to do.

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

Go ahead and upload this code to your Arduino, again if you are having trouble doing so see my post on [setting up your computer][setting_up_your_computer_post].


[setting_up_your_computer_post]: {% post_url 2016-05-19-setting-up-your-computer %}
[breadboard_primer]: {% post_url 2016-05-19-breadboard-primer %}
[led_primer]: {% post_url 2016-05-19-led-primer %}
