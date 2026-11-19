# Teensy 8k Input Lag Tester - by buddman69

**THIRST8kINPUTTESTER** is firmware for a **Teensy 4.1** that turns it into an input lag tester.
It presses buttons and moves sticks on a controller at exact times, timed on the Teensy's own
crystal at 8000 Hz, and the companion Windows app measures how long each press takes to reach a
game.

- Works with any USB controller: XInput or HID, 1000 Hz to 8000 Hz.
- Four channels (Teensy pins 1-4), each wired to any button or stick signal. The app works out
  which pin is which, so the wiring is up to you.
- Measures from the moment the line changes to the moment a game would see it, matched to the PC's
  clock to within a few microseconds.

## Download

Get the `.hex` file from the [latest release](../../releases/latest).

## Load it onto the Teensy

1. Install PJRC's [Teensy Loader](https://www.pjrc.com/teensy/loader.html).
2. Open the `.hex` file in it.
3. Press the button on the Teensy. It programs itself and restarts as **THIRST8kINPUTTESTER**.

## Wiring

- Teensy **pins 1-4** to the button or stick signals you want to test, one signal per pin.
- Teensy **GND** to the controller's GND.
- Buttons are pulled to ground like a press. Stick signals are driven low and high to move the stick.

**The Teensy's pins are 3.3 V only.** Connect them only to 3.3 V signals, never to 5 V or a battery
line. Opening a controller and wiring into it is at your own risk.

## Use

Plug in the controller and the Teensy, open the companion app's **Testing** tab, and start the input
latency test. It identifies the wiring first, then runs the test and shows the results.

## Licence

The firmware is provided as a binary, free to use. It is not open source.

It is built with PJRC's Teensyduino core, whose licence notice is in [NOTICE.md](NOTICE.md) and
in each release.
