# Biasing

Biasing is the putting components around a device to set DC voltages at the various terminals allow us to take advantage of the AC characteristics of the device when the DC is at the given level.

A BJT, however is what we call a current controlled device. That means that the easiest way to mathematically describe how it works is by looking at the currents.

The biases can be used to make it so that the transistor works like this:
* take the current flowing into the base
* multiply it by the number called beta (or hFE in many datasheets)
* that is the current the the transistor is trying to pull into its collector

So the current flowing into the base plus beta times that current flowing into the collector go out together through the emitter.

