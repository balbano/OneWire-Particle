OneWire
=======

A port of the [PJRC OneWire library](https://www.pjrc.com/teensy/td_libs_OneWire.html) for Arduino to work for both the Particle Core and Photon

The initial port to the Core was done by [paste by TIDWELLTIMJ](http://pastebin.com/i1ypx0Qn). The initial paste was separated separated into multiple files by [krvarma](https://github.com/krvarma/Dallas_DS18B20_SparkCore).

I've added in support for the Photon. The main action of the port is in OneWire.h where the various fast versions of digitalWrite, digitalRead and pinMode are defined.

The Arduino library used defines for these and directly manipulated the bits/ports/masks for maximum speed. Tidwelltimj switched to using functions in the initial port, using the source from the Core firmware for digitalWrite(), etc., but removed the various safety checks for speed.

I moved the functions to the header file in the hopes that the compiler will inline them. I'm not totally clear how much speed is actually needed for OneWire. The way it is right now seems to work. There is a discussion of fast writes [on the particle forums](https://community.particle.io/t/photon-and-the-pin-map-challenge/12223), but it doesn't discuss fast reads or pinmode changes.
