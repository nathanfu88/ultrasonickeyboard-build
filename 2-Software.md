# Table of Contents

1. [Hardware](1-Hardware.md)
2. [Software](2-Software.md)
3. [Operate](3-Operate.md)

---

# Software
This projects uses an [Arduino Nano](https://store.arduino.cc/usa/arduino-nano) to perform the basic logic for the different input/output systems. The Arduino family uses an IDE aptly named the [Arduino IDE](https://www.arduino.cc/en/Main/Software) to develop programs and write to the Arduino-based microcontrollers.

## Install the Arduino IDE
Download the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for your OS platform. If you want to, contribute, or just download the software.

The installer is sizeable at around 180 MB, and the file hosts aren't exactly fast...so give it a few minutes.

## Clone the Project Repository
Clone the following GitHub repository to get all the project files. Run the following snippet in Terminal or Command Prompt/GIT Bash. Make sure your current working directory is in a place you can access easily (ike your `home` or `My Documents` folder).
```
git clone https://github.com/nathanfu88/UltrasonicKeyboard.git
```

The project files are all available for you to use, modify, or hack. Feel free to explore!

## Uploading a Program to the Arduino
Connect the Arduino on the breadboard to a USB port on your computer using the USB-to-mini-USB cable.

### Confirming IDE Settings
Open the folder where you cloned the repository from [Clone the Project Repository](#clone-the-project-repository). In the `ultrasonickeyboard` folder, open the `ultrasonickeyboard.ino` file. The `.ino` extension is used by Arduino IDE, but it really just is a text file.

When the file opens in Arduino IDE, you have to specify some settings so your computer knows how to communicate with the desired microcontroller board. Go through Arduino IDE toolbar and confirm these settings:
- [ ] `Tools` > `Board: "Arduino Nano"`
- [ ] `Tools` > `Processor: "ATmega328P (Old Bootloader)"`
- [ ] `Tools` > `Port: "/dev/cu.usbserial-14410"`
- [ ] `Tools` > `Programmer: "AVRISP mkII"`

> _Note: If you don't see `/dev/cu.usbserial-14410`, your computer does not recognize the Arduino, either because of a poor connection or lack of driver. First, try unplugging and plugging the USB cable, or a different USB port on your computer. If the issue persists, you might need a driver. On Windows, download and install the Windows version of the [CH340 driver](https://sparks.gogo.co.nz/ch340.html). On Mac OS X, try [this driver](https://github.com/adrianmihalko/ch340g-ch34g-ch34x-mac-os-x-driver/raw/master/CH34x_Install_V1.5.pkg)_

> _Note: Your Arduino may not be using the CH340 USB-to-Serial chip. In that case, the drivers above may not work for you. You will have to do a little digging online to determine if you can find which chipset your particular Arduino utilizes_

### Verifying Code (Optional)
Arduino IDE has a process called `Verify` ![verify](img/verify.png), which is effectively compiling your software. The `Upload` process already goes through the verify stage before uploading the program to the Arduino, so this step is a little extranenous for us.

However, this is helpful if you just want to check your code, or just build the binary to program an Arduino at a later date.

### Upload
If all the settings are correct, click the `Upload` button.
![upload](img/upload.png)

Arduino IDE will compile the program and install it on the connected Arduino.

> _Note: The program will run as soon as it finishes uploading. If your ultrasonic sensor is close enough to an object, the speaker will start emitting sounds. It would be a good idea to confirm your environment before uploading the program. Either turn the sensor face down, or make sure its path is clear. It's not really a problem if your speaker makes noises immediately - it's just that it can be a little surprising if you are not expecting it. (And you can minimize noise pollution by taking the proper precautions)_

# Software Complete!
You're pretty much all done. However, you can move on to [Operate](3-Operate.md) to get a feel for how to use the keyboard, as well as some tips and things you can try.