# Table of Contents

1. [Hardware](1-Hardware.md)
2. [Software](2-Software.md)
3. [Operate](3-Operate.md)

---

# Operate
At this stage, you can really just explore what has been put together. Using the "keyboard" is (hopefully) pretty intuitive, but you might need to go through some additional steps to get a better experience.

## Calibrate
There's a minimum distance that's needed for the ultrasonic sensor to report decent measurements. The HC-SR04's documentation says the minimum distance is 2cm, but we're adding a little more buffer room.

Some of you may have a mount with a plastic extension that is very close to the distance your keyboard should be from the ultrasonic sensor. If you got a mount with a shorter extension, you'll have to manually "calibrate" the position of the C4 starting note.

To do this, place a solid object (hereforth referred to as a "reflector") right up to the sensor and slowly move it away. The speaker will play a sound when you're at the minimum distance. Take note of this distance - that is where your C4 from your keyboard should go. The distance between the rest of your keys should be static.

> _Note: Once you have the minimum distance, it might help to tape down your paper keyboard to prevent any shifts from throwing everything off_

> _Note: For best results, your sensor should be pointing along a perpendicular axis across the keyboard (or as perpendicular as possible). If the sensor is angled, all your readings will be skewed_

## Playing Notes
Place your reflector over the desired key on the keyboard printout. This will change the distance reading on the ultrasonic sensor, which then has a range of distances mapped to a particular frequency (musical note). A larger, flat surface works best, as any bends in the reflector can scatter the ultrasonic waves so that the reader is less likely to detect them.

## Play a Melody!
After you establish some understanding for how the keyboard works, try playing a few melodies and see if you can guess out what they are.

To play a melody, position your reflector over the proper notes, lifting the reflector up (in the Z-axis) to unobstruct the sensor so it plays no sound between notes.

### Melody 1
C4, C4, G4, G4, A4, A4, G4
F4, F4, E4, E4, D4, D4, C4
G4, G4, F4, F4, E4, E4, D4
G4, G4, F4, F4, E4, E4, D4

### Melody 2
G4, G4, G4, D#4, F4, F4, F4, D4
G4, G4, G4, D#4, G#4, G#4, G#4, G4
D#5, D#5, D#5, C5, G4, G4, G4, D4
G#4, G#4, G#4, G4, F5, F5, F5, D5

### Melody 3
E5, E5, E5, C5, E5, G5, G4
C5, G4, E4, A4, B4, A#4, A4
G4, E5, G5, A5, F5, G5, E5
C5, D5, B4 

### Melody 4
F#4, A4, C#5, A4, F#4, D4, D4, D4
C#4, D4, F#4, A4, C#5, A4
F#4, E5, D#5, D5
G#4, C#5, F#4, C#5
G#4, C#5, G#4, F#4, E4
C4, C4, C4
C4, C4, C4 

## What Next
As evident from trying to play some melodies, this particular project is not meant to actually be used as a legitimate piano replacement. The idea was to take a concept (playing the piano) and reimagine what it could look like from another perspective (using ultrasound and distance to emit frequencies) to create a different kind of learning experience.

That being said, feel free to explore the code, mess with the circuit (Can you improve it? Want to add more octaves? Add chord support?), or call it a day. The next few sections highlight some pieces of this project that were maybe overlooked, or weren't didn't really require a deep understanding of to get everything to work.

### Mute Circuit
The result of a pushbutton circuit is connected to pin D6 on the Arduino Nano as an input. The Nano will read this input and can mute the speaker. The on-board Nano LED will also light up to indicate if the speaker is muted.

Pushbuttons traditionally work as "ON while button is pressed, OFF while button is not pressed", but using some logic in the Arduino's code, we can reconfigure this pushbutton to function as "push ON, push again OFF". This works by detecting a "debounce", which is the change in the pushbuttons state, to trigger an action (mute or unmute).

The circuit for the pushbutton uses a [pull down resistor](https://playground.arduino.cc/CommonTopics/PullUpDownResistor). This is a common practice in electrical circuits, but we don't need dive too deep into that now. You can always search `pull down resistor` or `pull up resistor` to find more information online.

### Review the Code
You can look at the code to see how it works. The programming language for Arduino is C++ based, but there are some Arduino-specific conveniences the IDE provides to make it easier to work with the Arduino. The code is commented to explain what sections of code do.

There is a [debug branch](https://github.com/nathanfu88/UltrasonicKeyboard/tree/debug) of the code that will output information to the Arduino IDE [Serial Monitor](https://www.arduino.cc/en/guide/environment#toc12). You can look up how to use the serial monitor online.

The serial monitor is very helpful when trying to figure out what an Aruduino program is doing.

> _Note: Here's a tip if you're playing with the code - mute the circuit with the pushbutton (or through the code)_

### Play Melodies Automatically
The same circuit used for this project can be used for another project that can play melodies using just the speaker and basic notes. Check out the [ultrasonickeyboardmelodies repository](https://github.com/nathanfu88/UltrasonicKeyboardMelodies).

You can leave the circuit the same as built in the [Hardware](1-Hardware.md) section (you can technically remove the HC-SR04, as it isn't used in that project). Follow the same steps in [Software](2-Software.md) to upload the `ultrasonickeyboardmelodies` to the Arduino Nano.

View the [README](https://github.com/nathanfu88/UltrasonicKeyboardMelodies/blob/master/README.md) of that project to get an understanding of how it works.

If you get a feel for how to "play" a melody automatically, take a crack at adding your own!

> _Note: There is a [debug branch](https://github.com/nathanfu88/UltrasonicKeyboardMelodies/tree/debug) for this repository as well_