# WARNING

**I've never built or tested this. I don't recommend making one of these. It was noodling around.**

# Simple Module Tester

This is a simple Eurorack module tester that can be powered from 5V USB.

- It takes +5v from USB power, and turns it into +/-12v and also passes along the 5v. 
- The key component is a IR0512S DC-DC Converter from XP Power which [costs about £8.50 from Farnell](http://uk.farnell.com/xp-power/ir0512s/dc-dc-converter-semi-reg-dual/dp/1860988) and gives 125mA of power on both rails.  This is a standard SIP package, so other dual output DC-DC converters may work in the same spot. I just chose the one with a good output. 
- The board also includes some simple utilities to test your module with:
  - A square/triangle LFO for use as a clock source and CV input
  - A button that emits a gate from a jack when it is pressed
  - An input jack connected to a bipolar red/green LED for testing output
- Seems to work well with portable USB batteries. 
- The IR0512S is rated 125mA on +12v and -12v, but that seems quite conservative. A Dixie+Turing+Radio Music ran quite happily, with an expected current draw of 160mA on +12v, 52mA on -12v. The converter module was warm but certainly not hot. The whole thing was drawing 600mA from the USB port. 

It is based on Tom Whitwell's [Stupid USB Power][stupidusbpower].

[stupidusbpower]: https://github.com/TomWhitwell/StupidUSBPower

## WHY?

Because you shouldn't test a brand new DIY Euro module by plugging it into $$$ of modular synth. You should test it in isolation.

If you don't have a bipolar bench power supply, that can be hard.

This board seeks to help: it gives you some power outlets for both Eurorack modules and 1U Tiles, some input/output tools to debug CV and gate inputs and outputs, and it's easy to run from battery power.

If you want something more sophisticated, [Olivier Gillet's Module Tester][oliviertester] does a whole lot more and is more refined. It's also more expensive and complex to build.

[oliviertester]: https://github.com/pichenettes/module_tester

## TODO

* add diode/cap/fuse protection
* add two keyed headers
* add M4 standoffs
* make beautiful / useful silkscreen.

## USAGE

1. Seriously: **do not plug this into your computer**. Plug it into a USB battery pack or a mobile phone style mains adaptor
2. **DO NOT PLUG THIS INTO YOUR COMPUTER**

##Tom Whitwell's Reasons why this is stupid: 
1. There are no fuses or protection devices anywhere in the circuit. If you plug this plus $800 worth of modules into a $2000 laptop, you're taking a risk. NB: Do not do this. 
2. There is no filtering in the system, so there will be clock noise from the converter on the rails. The datasheet and my measurements suggest it's in the 60-85khz range. Do not use this to play live or record your new album. 
3. 125mA isn't very much power. Just because the module seems to run above that rating doesn't mean it's safe or reliable.  
4. Keyed headers are not reverse power protection. 

##Status 
- This project is Creative Commmons Licensed [CC-BY-SA](https://creativecommons.org/licenses/by-sa/3.0/). If you like the idea, why not develop it a little and submit your changes here? 
- I haven't exported a formal BOM. The only non-obvious bits aside from the DC-DC converter are: 
    - [USB Socket Type A, Through Hole](http://uk.farnell.com/multicomp/mc32603/usb-2-0-type-a-plug-th/dp/1696544)  
    - [Lumberg  150309 Stereo Socket](http://uk.farnell.com/lumberg/1503-09/connector-rca-jack-3-5mm-3way/dp/1243244)
    - [Amphenol  T821116A1S100CEU  Shrouded headers](http://uk.farnell.com/amphenol/t821116a1s100ceu/header-vertical-2-54mm-16way/dp/2215308)  
    - [Thonkiconn](http://www.thonk.co.uk/shop/thonkiconn-3-5mm-jack-sockets-x50/) mono jack socket, [Alpha](http://www.thonk.co.uk/shop/ttpots/) Pot, 3mm LEDs, 2k LED Resistors, 47uF 16v capacitor on the 5v line. 
