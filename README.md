# Open Organ

An open hardware/software multi-instrument (organ-focused) keyboard.

_This project doesn't exist. It's just an idea for now._


## Rationale

There are some cool commercial keyboards out there (I really like the general design of Crumar's Mojo keyboards), but it feels like nothing checks _all_ the boxes.
Some keyboards (Crumar Mojo Classic/Suitcase) are great organs but have no capacity to support other sounds.
Some keyboards (Roland VR-730, which I own), are good organ keyboards and sample players, but have horrible MIDI behaviors.
Some keyboards do lots of things well but cost far too much.
Some keyboards have great sounds but terrible phyisical controls.

I'd really like to be able to load arbitrary VST sounds into a physical keyboard.
Building my own sounds really hard, but maybe that's just because there isn't a great open software/hardware ecosystem around this specific product category.


## How it works

The following is initial speculation. 


### Hardware

A base specification for manufacturing components with consumer programmable manufacturing equipment (e.g. laser/water cutter, CNC machinery, 3D printers, ??) using commodity materials or parts.

* Chassis: Simple, flat design, ideally with a "suitcase" option, with mount points for all hardware. One and two-manual options?
* MIDI handler: Some black box which maps physical controls to MIDI which is sent to the CPU
* CPU: An x86 or ARM Linux computer for running software VSTs and other configuration software


#### Controls

* Keyboard manual(s): A well-known commodity keyboard (e.g. Fatar TP8/O) with alternative options.
  Specifications for modifications, e.g. replacement springs.
* Drawbar controls: Lower, upper, pedal
* Knobs: output volume, overdrive, ?? 
* Switches: 
    * Roto speaker on/off
    * Roto fast/slow
    * ???
* Inputs/outputs:
    * MIDI I/O
    * Stereo line out
    * Ethernet to SSH?
* Special controls
    * 6-way chorus/vibrato
    * Instrument selection interface: Perhaps each instrument is assigned a number and displayed on a 7-segment display.
      Perhaps a numpad, or up/down control for each digit, or a rotary encoder for selecting instrument?
      Perhaps support A/B/C/D preset buttons, with an indicator light if a preset is selected, and hold the button to change the preset?


### Software

#### Operating system

Linux. Run Windows VSTs with yabridge(?).

SSH + VNC installed/enablable for interactive configuration.


#### MIDI management

Perhaps physical control -> MIDI management could look like compiling firmware for a QMK computer keyboard?
I think there are more modern alternatives that don't require a compile step to reconfigure (ZMK?).
It would be cool to be able to configure this somewhat like I configure my Uno-modded FCB1010.


#### VST management

* A base set of free VSTs, like Zynthian, available by default.
* A schema for representing mappings between MIDI signals from the hardware to VST controls.
  Easily shareable, perhaps with a way to pull configs from Git repositories.
  * What about a way to represent VST routing?
    E.g. sidechain effects, or instruments that take an audio signal + MIDI signal (e.g. harmonizers)?
    It would be awesome to take a line-level vocal signal or other instrument signal for effects which require multiple inputs.
    It would _also_ be awesome if we could separately process the multiple input signals, e.g. playing keys with a guitarist and vocalist and managing processing in one unit.
* Ability to load VSTs from flash drive if formatted correctly?
* Ability to view VST GUIs on tablet/phone with VNC enabled.


## Prior art / inspiration / reference

* [Zynthian](https://zynthian.org/)
* [Belleart Wiki](http://www.belleart.org/belleartwiki/index.php/Main_Page)
