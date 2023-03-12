# Voltage and Current Sources

This file explains ideal voltage and current sources. Real world sources are not ideal, but in many cases the ideal form is good enough.

A voltage source is a "component" that always has a voltage across it. The current it outputs is whatever it needs to be to ensure that the voltage across it is the voltage. So if I connect a 1V voltage source to a 1 ohm resistor, an ideal voltage source will output 1A. If I change the resistor to 1kOhm, then it will output 1mA.

We call it a voltage source, but it really is a component that sources whatever current is needed to ensure that its own voltage is the expected voltage.

Voltage sources are relatively easy to wrap your head around because we have electrical outlets in our walls that provide an expected voltage. We have 12V batteries in our cars, 9V batteries in our smoke detectors, and cascaded 1.5V batteries in our electronics.

Current sources work in the exact same way as voltage sources, except that they output a fixed current and change their voltage as needed to ensure that the current output is what the current source says it will output.

These are much less intuitive because you can't just go to the store and buy a current source. You can't really even go to DigiKey and just buy a part that pushes out a certain current until it runs out. It's not a part type we feel. And indeed, a current source is really just a mathematical construct. It makes the math work in certain circuits. One of those circuits is a BJT.

The key to understanding a current source is that it will develop whatever voltage it needs to to ensure that the current flows. So we can imagine a 2mA current source across a 3 ohm resistor. In order for 1mA to flow through that resistor, the voltage across the resistor needs to be 0.06V. So the current source will produce, across itself, a 0.6V voltage.

