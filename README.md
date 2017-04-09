# HD120-Controller
Arduino sketch to act as a custom controller for Corsair HD120 RGB Fans

Copyright 2017 Kit Parenteau

Version score: 0.1.1.0

The lighting controller that comes standard for HD120 RGB fans left something to be desired.
This code allows a 5V Arduino AVR to be used as a controller for the fan lighting.
* An Arduino Micro or Micro Pro is recommended due to its physical size and hardware capabilities
* FastLED Library 3.1 or newer, and Arduino.cc IDE 1.8.1 or newer are required.

This is the initial version of this software. It is -NOT- the same as the video, which uses demo code to control the lights globally. I will hopefully implement some of the video functions as modes. 

Consider this to be an ALPHA version. Some assembly required. Do not taunt code. Comments may cause sweating or blindness.

User Features
* Software controlled (Currently by Serial communications)
* Control individual fans.
* Global Brightness Control
* Multiple Modes (And more to come)

Coder Features
* Remapping of the fans to putthe first LED in the proper place
* Mapping per sides of fans
* Mapping per quadrant of fan
* Uses FastLED - 8-bit mapped stuff makes things easy


Changelog
0.1.1.0 - February 6, 2017
* ADDED: Two more fan modes
* ADDED: Local compile size tracking in comments
* IMPROVED: Cleaned up code and increased comment clarity

Controls:
Open Serial connection to Arduino (115200 Baud)
- For example, use Serial monitor
- If using serial monitor, use Newline line ending setting
Send ">#,#,#" as Group,Setting,Value, for example,
>0,0,255  -> Sets the global brightness to full blast.
The ">" character is used as a wake header for the controller and will cause it to pause briefly to listen and respond with "Go"
An accepted command will respond with OK and then the three values it recorded.

Current groups:
0   -> Global
1-6 -> Each fan

Global Settings:
0   -> Brightness - 0-255
1   -> Frame loop counter. No reason to touch this most of the time.
2-7 -> Not currently used

Fan settings:
0   -> Mode
1-7 -> Mode-dependent

Modes:
0 -> Angry Myia Mode - Cycle from teal to red and back, approx 10 sec per cycle
Settings: 
None. Not-configurable.
ToDo: Consider confiiguration options.

1 -> Static Color
Settings:
1 -> Hue (FastLED 0-255 Hue, not 0-360. See Note 1 below.)

2 -> Single Color Pulse
Settings:
1 -> Hue
2 -> BPM (60/BPM = Time to pulse)

3 -> Rotating full rainbow per fan
Settings:
None.
ToDo: Consider direction/speed

4 -> Cycle full fan through rainbow and back in ten seconds
Settings:
None.
ToDo: Consider BPM options.

5 -> Rainbow Sparkles - Same as 3 Plus Sparkles
Settings:
1 -> Chance per frame of a sparkle, 0-255

Note 1:
Hue Chart:
https://raw.githubusercontent.com/FastLED/FastLED/gh-pages/images/HSV-rainbow-with-desc.jpg
0   -> Red
32  -> Orange
64  -> Yellow
96  -> Green
128 -> Aqua/Teal
160 -> Blue
192 -> Purple
224 -> Pink
255 -> Red
