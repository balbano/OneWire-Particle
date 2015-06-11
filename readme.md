USE THIS INSTEAD:
=================

This is OneWire library available on the particle web IDE, so this should be considered the most official one: https://github.com/Hotaman/OneWireSpark

I will be doing any further work in my fork of the above library: https://github.com/balbano/OneWireSpark

Don't use this repo! Use one of the two above.

OLD README:
===========

OneWire
-------

A port of the [PJRC OneWire library](https://www.pjrc.com/teensy/td_libs_OneWire.html) for Arduino to work for both the Particle Core and Photon


How it works
------------

The Arduino library used defines for these and directly manipulated the bits/ports/masks for maximum speed. Tidwelltimj switched to using functions in the initial port, using the source from the Core firmware for digitalWrite(), etc., but removed the various safety checks for speed.

The main action of the port is in Particle-OneWire.h where the various fast versions of digitalWrite, digitalRead and pinMode are defined.

The port to the Photon moved these functions to the header file in the hopes that the compiler will inline them.

Areas for improvement
---------------------

The way it is right now seems to work in a very basic test with 1 DS18B20 temperature sensor, but it's not clear if the current port is fast enough for all uses.

There is a discussion of fast writes [on the particle forums](https://community.particle.io/t/photon-and-the-pin-map-challenge/12223), but it doesn't discuss fast reads or pinmode changes, so if there is a problem with the library being too slow, the first place to look into improving is the reads and pinmode changes.

Contributors
------------

The initial port to the Core was done by [paste by TIDWELLTIMJ](http://pastebin.com/i1ypx0Qn). The initial paste was separated separated into multiple files by [krvarma](https://github.com/krvarma/Dallas_DS18B20_SparkCore).

Initial support for the Photon was done by [Brendan Albano](https://github.com/balbano/). [cdrodriguez](https://github.com/cdrodriguez/) fixed some issues with the Core and formatted the library for Web IDE use.
