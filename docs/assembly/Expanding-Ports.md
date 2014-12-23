Expanding the ports: Instructions
=================================

- I assembled my first emulator using mame4all as described in the AdaFruit article
    - https://learn.adafruit.com/downloads/pdf/retro-gaming-with-raspberry-pi.pdf
- however I noticed that this was only 1P, and only 2 buttons!
    - I wanted coin buttons, and Start buttons, and Esc/Pause buttons...
- fortunately someone had already written software for expanding the number of available pins using a MCP23017
    - to see the difference see the chart at RPi-Rev2-GPIO-versions.pdf
    - as you can see via color-coding, the two schemes are NOT COMPATIBLE
        - example: pin 19 is GPIO10, used for "UP" Joystick on the original scheme, but KEY_P = PAUSE on the expanded scheme

Different board pinouts
-----------------------

I'll assume you have the same pinout as me, which is Rev2.

How did I know this?  How can you find out yours? Run this:

    $ cat /proc/cpuinfo


Mine says Revision is "000e" , which is board B Rev 2

Reading:

- http://raspi.tv/2013/rpi-gpio-basics-2-how-to-check-what-pi-board-revision-you-have
- http://elinux.org/RPi_HardwareHistory

Reading the code
----------------

- Reading retrogame.c is a bit confusing!
- the pin numbers, as in ioStandard[] , refer to the GPIO index, NOT the harware pin order
    - example: 25, KEY_LEFT, is not at the end of the 26-pin chip
        - it is on the right edge a few pins up.  Why?  I don't know.  Ask the RPi designers!
    - example: 7 KEY_LEFTALT is actually at the bottom right corner



