# Teensy 8k Input Lag Tester - by buddman69

Measures real input latency on any USB controller. A **Teensy 4.1** running the
**THIRST8kINPUTTESTER** firmware presses the controller's buttons and moves its sticks at exact
times, timed on its own crystal at 8000 Hz, and the **Teensy 8k Input Lag Tester** app for Windows
times how long each press takes to reach a game.

- Works with any USB controller: XInput or HID, polled at 1000 to 8000 Hz (detected automatically).
- Four channels (Teensy pins 1-4), each wired to any button or stick signal. The app works out
  which pin is which, so the wiring is up to you.
- Measures from the moment the line changes to the moment a game would see it, matched to the PC's
  clock to within a few microseconds, and splits each press into the controller's part and
  Windows' part.
- Edge tracker: finds each input's best case and where its report cut-off sits, and follows it
  for the whole run.
- Also in the app: USB port check, PC power settings, USB polling trace and monitor, report
  content and ping.
- The app keeps itself and the Teensy up to date: it offers new versions of the app, and flashes
  the Teensy with the firmware it carries.

## Download

From the [latest release](../../releases/latest):

- `Teensy-8k-Input-Lag-Tester-Setup-<version>-beta.exe`: the app, with the Teensy firmware included.
- `THIRST8kINPUTTESTER-<version>.hex`: the Teensy firmware on its own.

The app is a beta for Windows 10 and 11, 64-bit. It is not code-signed yet, so Windows may say it
*protected your PC*: choose **More info**, then **Run anyway**.

## Load the firmware onto the Teensy

From the app (0.2.0 and later), in **Input latency**, under *Teensy firmware*:

- **A new Teensy 4.1, or one running something else:** click **Flash a new Teensy**, then press
  the button on the Teensy. The app writes the firmware, restarts the Teensy and checks it runs
  exactly what was sent.
- **A Teensy already running THIRST8kINPUTTESTER:** the app says when it carries a newer version;
  click **Update**. From 1.1.0 on, no button press is needed. (1.0.0 needs the button once.)

Or with PJRC's [Teensy Loader](https://www.pjrc.com/teensy/loader.html): open the `.hex` file (the
installer puts it in the Start menu under *Teensy firmware*) and press the button on the Teensy.

## Updates

The app checks this page's latest release when it starts. When there is a newer one, the button
at the top right says **Update to x.y.z**: it downloads the installer, checks it against the
release's SHA-256 checksum, installs it and reopens the app. (0.1.0 has no updater: install 0.2.0
once by hand.)

## Wiring

- Teensy **pins 1-4** to the button or stick signals you want to test, one signal per pin.
- Teensy **GND** to the controller's GND.
- Buttons are pulled to ground like a press. Stick signals are driven low and high to move the stick.

**The Teensy's pins are 3.3 V only.** Connect them only to 3.3 V signals, never to 5 V or a battery
line. Opening a controller and wiring into it is at your own risk.

## Use

Plug in the controller and the Teensy, open the app, pick the controller at the top and run
**Input latency**. It identifies the wiring first, then runs the test and shows the results.
With *Windows' USB timing* on (the default), Windows asks for administrator rights at the start of
each test.

## Licence

The app and firmware are provided as binaries, free to use. They are not open source.

The firmware is built with PJRC's Teensyduino core, whose licence notice is in
[NOTICE.md](NOTICE.md) and in each release.
