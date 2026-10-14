<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/logo.png?v=055f2b70" alt="Loophole app icon: a black hole with a lit rim on a dark rounded tile." width="128"></p>

<h1 align="center">Loophole</h1>

<p align="center"><b>Uploads that work first time, every time.</b><br>A companion for the official Arduino IDE.</p>

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/hero.gif?v=d003cda1" alt="The notch shows a board and a green dot. A card springs open: Port busy, a Python program is using your board. Loophole frees the port, and the card turns green with Connected, UNO R4 WiFi, Ready to upload, then folds back into the notch." width="640"></p>

<p align="center"><a href="https://github.com/IrtizaNasar/Loophole/releases/latest/download/Loophole.dmg"><b>Download for Mac</b></a><br><sub>macOS 14 or later · Arduino IDE 2.2 or later</sub></p>

> [!IMPORTANT]
> Loophole is an independent project. It is not made by, affiliated with or endorsed by Arduino.
>
> It is not a replacement for Arduino IDE. It runs alongside the official **Arduino IDE 2** (version 2.2 or later) and adds to it. You still write, compile and upload in Arduino IDE. It does not support VS Code, PlatformIO, the Arduino CLI, Arduino Cloud or the older Arduino IDE 1.

<p align="center"><a href="#what-it-does">What it does</a> · <a href="#reading-the-notch">Reading the notch</a> · <a href="#messages">Messages</a> · <a href="#upload-failed">Upload failed?</a> · <a href="#install">Install</a> · <a href="#supported-boards">Supported boards</a> · <a href="#settings">Settings</a> · <a href="#privacy">Privacy</a> · <a href="#questions">Questions</a> · <a href="#limits">Limits</a> · <a href="#why-it-exists">Why it exists</a> · <a href="#future">Future</a></p>

## What it does

Your Mac's notch shows when your board is ready to upload, and fixes it when it isn't.

Most failed uploads have nothing to do with your code. The port is wrong, another program is holding it, the board setting does not match, or Arduino IDE froze.

Loophole runs alongside Arduino IDE and adds what it lacks: a live view of the connection, and one-click fixes. It watches the board, the cable and Arduino IDE, shows the state in the notch, fixes what software can fix, and tells you plainly what to do about the rest.

It was built in a physical computing classroom at the UAL Creative Computing Institute. [Why it exists](#why-it-exists).

## Reading the notch

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ready-strip.png?v=265d590f" alt="The strip: a board on the left of the notch and a green dot on the right." width="300"><br><b>Strip</b></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ready-card.png?v=90e77a0e" alt="The card: Connected, UNO R4 WiFi, Ready to upload, and three facts." width="420"><br><b>Card</b></td>
</tr>
</table>

The **strip** is always visible while Arduino IDE is open: your board on the left, a green dot or a short word on the right.

The **card** opens when you point at the strip. It shows the state, one sentence, three facts and, when there is something to do, a button. It also opens by itself when something needs you, and briefly when you plug a board in.

| Colour | Meaning | What you do |
| --- | --- | --- |
| Green | Ready | Upload |
| Amber | Loophole or Arduino IDE is working | Wait |
| Yellow | Another program has the port | Press the button |
| Orange | An Arduino IDE setting does not match the board | Press the button |
| Blue | Arduino IDE is stuck | Press **Restart Arduino IDE** |
| Red | Cable, power or hardware | Fix it by hand |
| Grey | No board found | Plug one in |

"Open sketch" on the card is the sketch in your Arduino IDE window, the one Upload would send. It is not what is running on the board.

## Messages

### All good

#### Connected

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ready-strip.png?v=265d590f" alt="Strip around the notch showing the board on the left and a pinging green dot on the right." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ready-card.png?v=90e77a0e" alt="Open card reading Connected, UNO R4 WiFi, Ready to upload, with the port, Monitor closed and the open sketch." width="420"></td>
</tr>
</table>

**Meaning.** Your Mac sees the board, Arduino IDE is set to it, and nothing is holding the port.

**Fix.** None. Upload.

#### Connected, Serial Monitor open

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/monitor-strip.png?v=b34b9abe" alt="Strip around the notch showing the board and a green dot." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/monitor-card.png?v=82cfa3c7" alt="Open card reading Connected, Monitor open, with a grey Close Serial Monitor button." width="420"></td>
</tr>
</table>

**Meaning.** The Serial Monitor is open in the window you are using. Arduino IDE releases the port by itself when you upload from that window.

**Fix.** None. The grey **Close Serial Monitor** button is optional.

#### Uploading

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/uploading-strip.png?v=6ce6035f" alt="Strip around the notch showing the board and the amber word Uploading." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/uploading-card.png?v=c5e410be" alt="Open card reading Uploading to your UNO R4 WiFi, Leave the cable alone for a few seconds." width="420"></td>
</tr>
</table>

**Meaning.** Arduino IDE is sending your sketch to the board.

**Fix.** Leave the cable alone. It returns to green when the upload ends.

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/uploading.gif?v=9b09d6a1" alt="The word Uploading in the strip with light sweeping across it." width="340"></p>

### Loophole fixes these

#### Fixing the port

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/fixing-strip.png?v=659f829e" alt="Strip around the notch showing the board and the amber word Fixing." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/fixing-card.png?v=927329e0" alt="Open card reading Fixing the port, Pointing Arduino IDE at your UNO R4 WiFi." width="420"></td>
</tr>
</table>

**Meaning.** Arduino IDE was set to a port your board is no longer on. This is the usual cause of `No device found`, and it happens when you move the cable to another socket.

**Fix.** None. Loophole sets the right port in about a second.

#### Port busy: a program

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/busy-strip.png?v=b096cfb8" alt="Strip around the notch showing the board and the yellow words Port busy." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/busy-card.png?v=b7f8984e" alt="Open card reading Port busy, A Python program is using your board, with a red Stop the Python program button and a grey Check again button." width="420"></td>
</tr>
</table>

**Meaning.** Only one program can talk to a board at a time. A script or a Terminal window got there first, so the upload would fail.

**Fix.** Press **Stop the …**. It ends that program, so run it again afterwards if you need it.

#### Port busy: an app

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/app-strip.png?v=b096cfb8" alt="Strip around the notch showing the board and the yellow words Port busy." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/app-card.png?v=df82e4be" alt="Open card reading Port busy, Serial Bridge is using your board, with a red Quit Serial Bridge button." width="420"></td>
</tr>
</table>

**Meaning.** Another serial app, such as a plotter, is connected to your board. The card names it.

**Fix.** Press **Quit …**. Loophole asks the app to quit normally, so save your work in it first.

#### Port busy: Serial Monitor in another window

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/otherwindow-strip.png?v=b096cfb8" alt="Strip around the notch showing the board and the yellow words Port busy." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/otherwindow-card.png?v=4889fd2e" alt="Open card reading Port busy, Serial Monitor is open in the window Blink, with a Close Serial Monitor button." width="420"></td>
</tr>
</table>

**Meaning.** You opened the Serial Monitor in one Arduino IDE window and pressed Upload in another. Arduino IDE only closes the Monitor in the window you upload from.

**Fix.** Press **Close Serial Monitor**. Your sketches stay open.

#### Port busy: FTDI board

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ftdi-strip.png?v=b096cfb8" alt="Strip around the notch showing the board and the yellow words Port busy." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ftdi-card.png?v=3edb84de" alt="Open card reading Port busy, Close the Serial Monitor tab, then upload." width="420"></td>
</tr>
</table>

**Meaning.** Boards with an FTDI USB chip, such as many Nano clones, cannot be uploaded to while the Serial Monitor is open.

**Fix.** Press **Close Serial Monitor**, upload, then reopen the Monitor.

#### Board package missing

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/package-strip.png?v=e279c2db" alt="Strip around the notch showing the board and the orange words Set up." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/package-card.png?v=fb57bdad" alt="Open card reading Board package missing, Arduino IDE can't use your UNO R4 WiFi yet, with an Install it for me button." width="420"></td>
</tr>
</table>

**Meaning.** Arduino IDE only knows the classic boards when first installed. Newer boards such as the UNO R4, Nano 33 and ESP32 each need a board package downloaded once. Until then the board is missing from **Tools > Board**.

**Fix.** Press **Install it for me**. Loophole downloads the package with Arduino IDE's own installer, restarts Arduino IDE once, then selects your board. It takes a few minutes and needs the internet. If the download fails, Loophole opens Boards Manager with the search filled in.

#### Wrong board

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/wrongboard-strip.png?v=f1d61407" alt="Strip around the notch showing the board and the orange words Wrong board." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/wrongboard-card.png?v=e036f536" alt="Open card reading Wrong board, Arduino IDE is set up for Nano 33 BLE, with a Switch to UNO R4 WiFi button." width="420"></td>
</tr>
</table>

**Meaning.** The port is right, but **Tools > Board** names a different board from the one plugged in. Arduino IDE's toolbar shows the board you last chose, not the board that is connected.

**Fix.** It depends on the board.

| Your board | Button |
| --- | --- |
| Official Arduino board | **Switch to …** changes the setting for you. |
| ESP32, Raspberry Pi Pico, Teensy | **Open Arduino IDE**, then pick your model in **Tools > Board**. Loophole knows the family, not the exact model. |
| Clone with a plain USB chip | **Open Arduino IDE**, then pick your board. Shown only when Arduino IDE is set to a board that cannot be a clone. |

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/wrongfamily-card.png?v=6eab9a1c" alt="Open card reading Wrong board, Arduino IDE is set up for UNO R4 WiFi, plugged in ESP32, with an Open Arduino IDE button." width="420"></p>

The UNO R4 WiFi and Nano ESP32 contain an Espressif chip. In firmware-update mode they appear as a bare ESP32. If that happens, unplug the board and plug it back in.

#### Wrong port

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/wrongport-strip.png?v=a39bc664" alt="Strip around the notch showing the board and the orange words Wrong port." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/wrongport-card.png?v=07a07329" alt="Open card reading Wrong port, Arduino IDE is on the wrong port, with Try again and Check again buttons." width="420"></td>
</tr>
</table>

**Meaning.** Arduino IDE is set to a different port from your board, and the automatic fix did not take.

**Fix.** Press **Try again**. If it stays orange, pick the port shown under "Board is on" in **Tools > Port**.

If the card says **Arduino IDE has lost track of its port**, the IDE is showing the port as selected but not using it. This happens when Arduino IDE was opened before the board was plugged in. Loophole normally corrects it by itself. If it cannot, press **Restart Arduino IDE**; picking the port again will not help.

#### Arduino IDE lost your ports

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/discovery-strip.png?v=cd7efe32" alt="Strip around the notch showing the board and the blue word Restart." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/discovery-card.png?v=ac036a47" alt="Open card reading Restart needed, Arduino IDE lost your ports, with a Restart Arduino IDE button." width="420"></td>
</tr>
</table>

**Meaning.** The part of Arduino IDE that finds ports has stopped. The Port menu is empty or greyed out even though the board is connected.

**Fix.** Press **Restart Arduino IDE**. It takes about 15 seconds and reopens your sketch.

#### Arduino IDE isn't responding

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/frozen-strip.png?v=cd7efe32" alt="Strip around the notch showing the board and the blue word Restart." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/frozen-card.png?v=372986e6" alt="Open card reading Not responding, Arduino IDE isn't responding, with a Restart Arduino IDE button." width="420"></td>
</tr>
</table>

**Meaning.** Arduino IDE froze, usually after the Mac slept with it open. Quit does not work in this state.

**Fix.** Press **Restart Arduino IDE**. Loophole asks it to quit, and force-quits after five seconds if it cannot.

### These need your hands

#### No board

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/noboard-strip.png?v=65a59ade" alt="Strip around the notch showing a faint board outline with a USB plug sliding towards it, and the words No board." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/noboard-card.png?v=84202b04" alt="Open card reading No board, No board plugged in." width="420"></td>
</tr>
</table>

**Meaning.** Your Mac sees no board on USB.

**Fix.** Plug the board in. If it is plugged in and its light is on, the cable is charge-only. Use a data cable.

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/noboard.gif?v=e076f6fb" alt="A board outline with a USB plug sliding towards its socket." width="340"></p>

#### Check the cable

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/cable-strip.png?v=79d13ec1" alt="Strip around the notch showing a faint board outline with a red USB plug, and the red word Cable." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/cable-card.png?v=8041d7a7" alt="Open card reading Check the cable, Your Mac can't see the UNO R3." width="420"></td>
</tr>
</table>

**Meaning.** Your Mac can tell something is on the USB socket but cannot talk to it.

**Fix.** Push the cable in firmly at both ends. Try another socket, then another cable, then another board.

#### USB port switched off

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/overcurrent-strip.png?v=085cceca" alt="Strip around the notch showing a faint board outline with a red USB plug, and the red word Cable." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/overcurrent-card.png?v=55760659" alt="Open card reading Check the cable, Your Mac switched the USB port off to protect itself." width="420"></td>
</tr>
</table>

**Meaning.** Something on the board drew more current than USB provides, typically a motor, servo or LED strip on the 5V pin.

**Fix.** Unplug the motor from the 5V pin, then unplug and replug the board. Power motors from their own supply.

#### Short circuit or too much load

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/short-strip.png?v=99c4aefb" alt="Strip around the notch showing a faint board outline with a red USB plug, and the red word Power." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/short-card.png?v=3d28c873" alt="Open card reading Short circuit?, Your Mac cut the power to your board." width="420"></td>
</tr>
</table>

**Meaning.** The board lost power because of a short or an overload. To a computer this looks the same as unplugging it, so Loophole checks your Mac's log for a USB power cut.

**Fix.** Unplug the board. Remove every wire from 5V, 3.3V, VIN and GND. Wait ten seconds and plug it back in. If it turns green, add the wires back one at a time until it turns red again.

#### Board went quiet

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/quiet-strip.png?v=bcd3e843" alt="Strip around the notch showing the words Reset board in red." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/quiet-card.png?v=c426be0e" alt="Open card reading Board went quiet, Your Nano 33 BLE went quiet after the upload, with advice to press reset twice and upload Blink." width="420"></td>
</tr>
</table>

**Meaning.** You uploaded a sketch and the board never came back. On boards with built-in USB, such as the Leonardo, Micro, Nano 33 and Nano ESP32, the sketch itself runs the USB connection. A sketch that crashes or hangs straight away takes the port with it, so the board disappears even though the cable is fine.

**Fix.** Press the board's reset button twice quickly. Its light pulses and the board waits for an upload instead of running the faulty sketch. Upload a sketch that works, such as **File > Examples > 01.Basics > Blink**, then find the problem in your own sketch.

#### Unstable board

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/unstable-strip.png?v=34a616e0" alt="Strip around the notch showing the board and the red word Unstable." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/unstable-card.png?v=5e352aab" alt="Open card reading Unstable board, Your board keeps disconnecting, with advice to press reset twice and upload Blink." width="420"></td>
</tr>
</table>

**Meaning.** The same board has dropped off and come back three times in thirty seconds. On boards with built-in USB, such as the Leonardo, Micro, Nano 33 and UNO R4, the sketch itself runs the USB connection. A sketch that crashes or hangs takes the port down with it, so the port appears for a moment and vanishes.

**Fix.** Press the board's reset button twice quickly. Its light pulses and the board waits for an upload instead of running the faulty sketch. Upload a simple sketch such as **File > Examples > 01.Basics > Blink**. If the board still drops off with Blink on it, treat it as a short circuit and check the wiring.

## Upload failed?

Match the error at the bottom of the Arduino IDE window.

| Arduino IDE says | Loophole shows | Fix |
| --- | --- | --- |
| `No device found on cu.usbmodem…` | Fixing, then green | Automatic. Upload again. |
| `can't open device … No such file or directory` | Fixing, then green | Automatic. Upload again. |
| `Resource busy`, `port busy` | Port busy | Press the button on the card. |
| `programmer is not responding` | Wrong board or Wrong port | Press the button. If green, remove wires from pins 0 and 1. |
| Board missing from Tools > Board, `Platform … is not installed` | Set up | Press **Install it for me**. |
| Port menu empty or greyed out | No board, Cable or Restart | Follow the card. |
| Window frozen after sleep | Restart | Press **Restart Arduino IDE**. |
| The board vanished right after an upload | Reset board | Press reset twice, then upload Blink. |
| The port appears for a second, then vanishes | Unstable | Press reset twice, then upload Blink. |
| macOS says "USB Accessories Disabled" | Power | Find the short. |
| Upload fails and Loophole is green | Green | The connection is fine. Read Arduino IDE's first error line: it is the sketch or the wiring. |

## Install

1. [Download Loophole.dmg](https://github.com/IrtizaNasar/Loophole/releases/latest/download/Loophole.dmg).
2. Open it and drag Loophole to Applications.
3. Open Loophole. It is signed and notarised by Apple, so macOS opens it without a warning.
4. On the welcome screen, press **Add the Arduino IDE helper**, then let Arduino IDE restart once.

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/welcome.png?v=da452056" alt="The Loophole welcome window: the app icon, a small preview of the notch strip, three short points, and the buttons Add the Arduino IDE helper and Not now." width="360"></p>

Loophole opens when you log in, so it is ready whenever Arduino IDE is. You can turn that off under **Open at login**.

Loophole keeps itself up to date. When a new version is out, it tells you and installs it with one click.

### The helper

A small add-on inside Arduino IDE that lets Loophole read and correct Arduino IDE's board and port settings. Loophole installs it and keeps it up to date. After an update, the card shows "Helper updated. Restart the IDE to finish." until Arduino IDE has been restarted once.

| | Without | With |
| --- | --- | --- |
| Connected, No board, Cable, Power, Port busy | Yes | Yes |
| Fixes a wrong port | No | Yes |
| Detects a wrong board or missing package | No | Yes |
| Detects a frozen Arduino IDE | No | Yes |
| Exact model names for ESP32 boards and clones | No | Yes |
| Close Serial Monitor | Frees the port | Closes the tab too |

## Supported boards

Any board that appears on your Mac as a USB serial port.

<table>
<tr>
<td align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ready-strip.png?v=265d590f" alt="Teal board picture." width="230"><br>UNO, Mega</td>
<td align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/nano-strip.png?v=7dbbd745" alt="Blue board picture." width="230"><br>Nano, MKR</td>
</tr>
<tr>
<td align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/esp32-strip.png?v=333b1481" alt="Black board picture with a silver can." width="230"><br>ESP32</td>
<td align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/pico-strip.png?v=9e70b14f" alt="Green board picture." width="230"><br>Raspberry Pi Pico</td>
</tr>
</table>

| Board | Name shown | Wrong board check | Package check |
| --- | --- | --- | --- |
| Official Arduino (UNO R3, UNO R4 Minima and WiFi, Mega 2560, Leonardo, Micro, Nano Every, Nano 33 IoT and BLE, Nano RP2040 Connect, Nano ESP32, Due, Zero, MKR1000, MKR WiFi 1010) | Exact, from the board | One-click switch | One-click install |
| ESP32 on built-in USB, Raspberry Pi Pico, Teensy | Family, then the model you choose in Arduino IDE | By family | Yes |
| Boards that report their own name (Adafruit, Seeed, micro:bit) | As reported | No | No |
| Clones with a CH340, CP210x or FTDI chip | The model chosen in Arduino IDE, or "board" | Limited | No |

No tool can read the exact model of an ESP32 or a clone over USB. Arduino IDE has the same limit. Loophole does not guess: an unrecognised device is shown as "board". Monitors and phones that appear as serial ports are ignored.

### Two boards at once

Loophole follows the board you touched last: the one you plugged in most recently, or whose port you picked in Arduino IDE. When you plug a board in, Loophole also points Arduino IDE at it.

## Settings

Right-click the notch, or click the menu bar icon.

- **Check again now**
- **Restart Arduino IDE**
- **Show on**: *Active screen* follows the screen you are working on (default). *Mac's built-in screen* keeps it on the notch.
- **Open at login**: on by default.
- **Check for Updates…**: Loophole also checks by itself once a day.
- **Install Arduino IDE helper…**
- **Quit Loophole**

The menu bar icon shows the state too: a filled hole is ready, an empty ring is no board, a dot above the hole needs you.

## Privacy

Loophole runs on your Mac. There is no account, and it never sends your sketches, files, ports or anything that identifies you.

Once a day it sends an anonymous count, so we can see how many Macs use Loophole and which problems come up most often. You can turn this off at any time with **Share anonymous usage count** in the menu.

<details>
<summary><b>Exactly what the daily count contains</b></summary>

<br>

| Included | Example |
| --- | --- |
| A random number made on your Mac, not linked to you | 30d4982f-… |
| Versions of Loophole, macOS and Arduino IDE | 1.0.0, 14.3, 2.3.10 |
| Whether the Arduino IDE helper is installed | yes |
| How often each Loophole message appeared | Port busy: 3 |
| Which fixes were used, and whether they worked | Switch board: worked |
| The kinds of board plugged in | UNO R4 WiFi |

The country and an approximate city are worked out from the connection when the count arrives. Your IP address is not kept, and the city is only ever stored as a total across everyone, never next to that random number.

</details>

<details>
<summary><b>Other ways Loophole uses the internet</b></summary>

<br>

- **Updates.** Loophole checks GitHub once a day for a newer version and downloads it only if you choose to install it.
- **Board packages.** Only when you press **Install it for me**, Arduino IDE's own installer downloads the package, as Boards Manager would.

</details>

<details>
<summary><b>What stays on your Mac</b></summary>

<br>

To do its job, Loophole looks at your USB devices and serial ports, which program is using your board's port, and Arduino IDE's window titles. Through the helper it reads the sketch name, board, port and installed packages that Arduino IDE has selected. The helper only accepts connections from your own Mac. Loophole keeps a few small settings files in your home folder and its random number in `/Users/Shared/Loophole`.

</details>

## Questions

**Will it close my work?** Only when you press a button that says so. "Stop the …" and "Quit …" end the named program. "Restart Arduino IDE" closes every Arduino IDE window and reopens your sketch.

**Does it change anything by itself?** Only Arduino IDE's port setting, the same as choosing it in Tools > Port.

**Does it work in full screen?** It stays hidden in full-screen apps unless something needs you.

**Does it check my code or wiring?** No. Green means the connection is good, not that the sketch compiles.

**How do updates work?** Loophole checks once a day. When a new version is out it shows what is new and installs it when you press **Install Update**, then reopens. You can also choose **Check for Updates…** from the menu. Every update is signed, and Loophole refuses one that is not.

**How do I remove it?** Quit Loophole and move it to the Bin. To remove the helper, delete `~/.arduinoIDE/plugins/loophole-bridge` and restart Arduino IDE.

## Limits

- One-click board switching and package install cover official Arduino boards.
- Wrong port, wrong board, missing package and frozen Arduino IDE fixes need the helper.
- Short-circuit detection is a strong hint, not a measurement.
- With several Arduino IDE windows open, Loophole cannot always tell which one holds the Serial Monitor, so it warns whenever one does.
- Works with the Arduino IDE 2 family. Tested on 2.3.10, the current release. The helper needs 2.2 or later; on 2.0 and 2.1 Loophole runs without it. Arduino IDE 1 is not supported.
- VS Code, PlatformIO and the Arduino CLI are not supported, and there are no plans to add them.

## Why it exists

Loophole grew out of the physical computing module I teach at the UAL Creative Computing Institute. My students kept losing time to uploads that failed for reasons that had nothing to do with their code. Debugging those problems with them shaped every message in this app. I am sharing it so that other students, teachers, hobbyists and tinkerers can benefit too.

## Future

Loophole is a Mac app today. In future we plan to separate its diagnosis logic from the Mac interface and build a similar app for Windows, and potentially Linux. There is no date for this.

---

<sub>Updates are delivered with <a href="https://sparkle-project.org">Sparkle</a>, used under the MIT licence.</sub>

<sub>Loophole is an independent project. It is not affiliated with or endorsed by Arduino. Arduino is a trademark of Arduino SA.</sub>
