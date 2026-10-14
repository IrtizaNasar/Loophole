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
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ready-strip.png?v=ccc41bf1" alt="The strip: a board on the left of the notch and a green dot on the right." width="300"><br><b>Strip</b></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ready-card.png?v=90e77a0e" alt="The card: Connected, UNO R4 WiFi, Ready to upload, and three facts." width="420"><br><b>Card</b></td>
</tr>
</table>

The **strip** is always visible while Arduino IDE is open: your board on the left, a green dot or a short word on the right.

The **card** opens when you point at the strip. It shows the state, one sentence, three facts and, when there is something to do, a button. It also opens by itself when something needs you, and briefly when you plug a board in.

| Colour | Meaning | What you do |
| --- | --- | --- |
| Green | Ready | Upload |
| Amber | Loophole or Arduino IDE is working | Wait. During a firmware update, **don't unplug the board** |
| Yellow | Another program has the port | Press the button |
| Orange | An Arduino IDE setting does not match the board, or the board stopped answering | Press the button |
| Blue | Arduino IDE is stuck | Press **Restart Arduino IDE** |
| Red | Cable, power or hardware | Fix it by hand |
| Grey | No board found | Plug one in |

"Open sketch" on the card is the sketch in your Arduino IDE window, the one Upload would send. It is not what is running on the board.

## Messages

### All good

#### Connected

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ready-strip.png?v=ccc41bf1" alt="Strip around the notch showing the board on the left and a pinging green dot on the right." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ready-card.png?v=90e77a0e" alt="Open card reading Connected, UNO R4 WiFi, Ready to upload, with the port, Monitor closed and the open sketch." width="420"></td>
</tr>
</table>

**Meaning.** Your Mac sees the board, Arduino IDE is set to it, and nothing is holding the port.

**Fix.** None. Upload.

#### Connected, Serial Monitor open

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/monitor-strip.png?v=bcff9554" alt="Strip around the notch showing the board and a green dot." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/monitor-card.png?v=82cfa3c7" alt="Open card reading Connected, Monitor open, with a grey Close Serial Monitor button." width="420"></td>
</tr>
</table>

**Meaning.** The Serial Monitor is open in the window you are using. Arduino IDE releases the port by itself when you upload from that window.

**Fix.** None. The grey **Close Serial Monitor** button is optional.

#### Uploading

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/uploading-strip.png?v=f7ea5e42" alt="Strip around the notch showing the board and the amber word Uploading." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/uploading-card.png?v=cd9f94a0" alt="Open card reading Uploading to your UNO R4 WiFi, Leave the cable alone for a few seconds." width="420"></td>
</tr>
</table>

**Meaning.** Arduino IDE is sending your sketch to the board.

**Fix.** Leave the cable alone. It returns to green when the upload ends.

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/uploading.gif?v=224990a0" alt="The word Uploading in the strip with light sweeping across it." width="340"></p>

### Loophole fixes these

#### Fixing the port

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/fixing-strip.png?v=44306e8d" alt="Strip around the notch showing the board and the amber word Fixing." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/fixing-card.png?v=e5d1c437" alt="Open card reading Fixing the port, Pointing Arduino IDE at your UNO R4 WiFi." width="420"></td>
</tr>
</table>

**Meaning.** Arduino IDE was set to a port your board is no longer on. This is the usual cause of `No device found`, and it happens when you move the cable to another socket.

**Fix.** None. Loophole sets the right port in about a second.

Each Arduino IDE window keeps its own board and port. With several sketches open, Loophole checks every window and fixes any that is set to a port your board is no longer on, so Upload works from whichever window you are in. A window set to a different board that is also plugged in is left alone.

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
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/package-card.png?v=d85eaf66" alt="Open card reading Board package missing, Arduino IDE can't use your UNO R4 WiFi yet, with an Install it for me button." width="420"></td>
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
| Adafruit, SparkFun, Seeed and other makers' boards with their own USB id, once their board package is installed | **Switch to …** changes the setting for you. |
| ESP32, Raspberry Pi Pico, Teensy | **Open Arduino IDE**, then pick your model in **Tools > Board**. Loophole knows the family, not the exact model. |
| Clone with a plain USB chip | **Open Arduino IDE**, then pick your board. Shown only when Arduino IDE is set to a board that cannot be a clone. |

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/wrongfamily-card.png?v=ee978466" alt="Open card reading Wrong board, Arduino IDE is set up for UNO R4 WiFi, plugged in ESP32, with an Open Arduino IDE button." width="420"></p>

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

**Fix.** Press **Restart Arduino IDE**. Loophole asks it to quit, and force-quits after five seconds if it cannot. (When Arduino IDE is working and only asking about unsaved changes, Loophole brings that question forward and waits for your answer instead.)

#### Board not answering

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/notanswering-strip.png?v=e78b58ef" alt="Strip around the notch showing the board and the orange words No answer." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/notanswering-card.png?v=026718ab" alt="Open card reading Board not answering, Your UNO R4 WiFi didn't answer the upload, with a Restart board button." width="420"></td>
</tr>
</table>

**Meaning.** UNO R4 WiFi only. Arduino IDE says `No device found on cu.usbmodem…`, yet your Mac still sees the board, so everything else looked green. The R4 WiFi has two chips: one talks to your Mac over USB and passes each upload on to the chip that runs your sketch. Sometimes, mostly on Macs, the two stop talking. It is a known problem with this board, not your code. Loophole spots it from the way the upload stops after less than a second, where a working upload takes several seconds.

**Fix.** Press **Restart board**, then upload again. Loophole restarts both chips through the USB cable, just like unplugging and plugging back in. It takes about five seconds and keeps the same port.

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/restartingboard-card.png?v=fe29d652" alt="Open card reading Restarting board, Restarting your UNO R4 WiFi, a few seconds, no need to unplug." width="420"></p>

If it happens again after a restart, the card suggests the next step:

| The board's USB firmware | The card offers |
| --- | --- |
| Older than 0.6.0 | **Update firmware** (below) |
| 0.6.0, the newest | **Restart board** again, and advice to plug into a different USB port |

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/notansweringagain-card.png?v=44edb12d" alt="Open card reading Board not answering, it happened again after a restart, the board's USB firmware 0.4.1 is out of date, with an Update firmware button." width="420"></p>

#### Updating firmware

> [!WARNING]
> **Don't unplug the board while the firmware updates.** Don't close the lid or let the Mac sleep either. If the update is cut off halfway, the board's USB chip can be left without working firmware, and the board then can't connect to any computer until it is repaired by hand.

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/updatingfirmware-strip.png?v=37e3017a" alt="Strip around the notch showing the board and the amber words Don't unplug." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/updatingfirmware-card.png?v=cbaac847" alt="Open card reading Updating firmware, Don't unplug your UNO R4 WiFi, with the firmware going from 0.4.1 to 0.6.0." width="420"></td>
</tr>
</table>

**Meaning.** The UNO R4 WiFi's USB chip runs firmware from Arduino, and older versions have upload problems that later ones fixed. Loophole reads the version over USB when the board is plugged in.

**Fix.** Press **Update firmware**, read the warning, then press **Update firmware** again. Loophole runs Arduino IDE's own firmware updater, the one behind **Tools > Firmware Updater**, and keeps the card on "Don't unplug" until it finishes. It takes about a minute and needs the internet. Loophole keeps the Mac awake meanwhile. Arduino's updater ends by asking for the board to be unplugged and plugged back in; Loophole does that step for you through the cable, then shows **Firmware updated** once the board reports the new version.

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/firmwareupdated-card.png?v=13aee95e" alt="Open card reading Firmware updated, Your UNO R4 WiFi is up to date, its USB firmware is now 0.6.0, upload yours again." width="420"></p>

Arduino's updater replaces the sketch on the board, so upload yours again afterwards. You can also start an update from the menu: **Update UNO R4 WiFi firmware…** appears whenever the board's firmware is out of date.

### These need your hands

#### No board

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/noboard-strip.png?v=d55f9ffa" alt="Strip around the notch showing a faint board outline with a USB plug sliding towards it, and the words No board." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/noboard-card.png?v=f8e26eea" alt="Open card reading No board, No board plugged in." width="420"></td>
</tr>
</table>

**Meaning.** Your Mac sees no board on USB.

**Fix.** Plug the board in. If it is plugged in and its light is on, the cable is charge-only. Use a data cable.

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/noboard.gif?v=0ea69b16" alt="A board outline with a USB plug sliding towards its socket." width="340"></p>

#### Check the cable

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/cable-strip.png?v=88f683de" alt="Strip around the notch showing a faint board outline with a red USB plug, and the red word Cable." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/cable-card.png?v=82cd1a61" alt="Open card reading Check the cable, Your Mac can't see the UNO R3." width="420"></td>
</tr>
</table>

**Meaning.** Your Mac can tell something is on the USB socket but cannot talk to it.

**Fix.** Push the cable in firmly at both ends. Try another socket, then another cable, then another board.

#### USB port switched off

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/overcurrent-strip.png?v=88f683de" alt="Strip around the notch showing a faint board outline with a red USB plug, and the red word Cable." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/overcurrent-card.png?v=4e3679a5" alt="Open card reading Check the cable, Your Mac switched the USB port off to protect itself." width="420"></td>
</tr>
</table>

**Meaning.** Something on the board drew more current than USB provides, typically a motor, servo or LED strip on the 5V pin.

**Fix.** Unplug the motor from the 5V pin, then unplug and replug the board. Power motors from their own supply.

#### Short circuit or too much load

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/short-strip.png?v=fa116841" alt="Strip around the notch showing a faint board outline with a red USB plug, and the red word Power." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/short-card.png?v=d0df68f3" alt="Open card reading Short circuit?, Your Mac cut the power to your board." width="420"></td>
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

#### Update mode

<table>
<tr>
<td width="42%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/othermode-strip.png?v=0ac40432" alt="Strip around the notch showing the board and the orange words Update mode." width="300"></td>
<td width="58%" align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/othermode-card.png?v=3fa6dc1b" alt="Open card reading Update mode, Your UNO R4 WiFi is in update mode, with advice to unplug it and plug it back in." width="420"></td>
</tr>
</table>

**Meaning.** A board Loophole knows is showing a different USB identity for more than a few seconds: its bootloader, a firmware-update mode, or a sketch that keeps crashing. Loophole recognises it by its serial number and keeps its usual name, rather than reporting a strange new board. An UNO R4 WiFi in this state appears on your Mac as a bare ESP32.

**Fix.** Unplug the board and plug it back in. If you started a firmware update on purpose, let it finish first.

## Upload failed?

Match the error at the bottom of the Arduino IDE window.

| Arduino IDE says | Loophole shows | Fix |
| --- | --- | --- |
| `No device found on cu.usbmodem…` | Fixing, then green | Automatic. Upload again. |
| `No device found on cu.usbmodem…` (UNO R4 WiFi) | Board not answering | Press **Restart board**, then upload again. |
| `No device found on cu.usbmodem…` (other boards) | Green | The board stopped answering, though your Mac still sees it. Unplug it and plug it into a different USB port, then upload again. |
| `can't open device … No such file or directory` | Fixing, then green | Automatic. Upload again. |
| `Resource busy`, `port busy` | Port busy | Press the button on the card. |
| `programmer is not responding` | Wrong board or Wrong port | Press the button. If green, remove wires from pins 0 and 1. |
| Board missing from Tools > Board, `Platform … is not installed` | Set up | Press **Install it for me**. |
| Port menu empty or greyed out | No board, Cable or Restart | Follow the card. |
| Window frozen after sleep | Restart | Press **Restart Arduino IDE**. |
| The board vanished right after an upload | Reset board | Press reset twice, then upload Blink. |
| The port appears for a second, then vanishes | Unstable | Press reset twice, then upload Blink. |
| macOS says "USB Accessories Disabled" | Power | Find the short. |
| Any other error while Loophole is green | Green | Your Mac, the port and the settings are fine. Read Arduino IDE's first error line: it is usually the sketch or the wiring. |

## Install

1. [Download Loophole.dmg](https://github.com/IrtizaNasar/Loophole/releases/latest/download/Loophole.dmg).
2. Open it and drag Loophole to Applications.
3. Open Loophole. It is signed and notarised by Apple, so macOS opens it without a warning.
4. Loophole adds its Arduino IDE helper straight away. On the welcome screen, press **Continue**. If Arduino IDE is open, let it restart once so it loads the helper.

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/welcome.png?v=5c8244c9" alt="The Loophole welcome window: the app icon, a small preview of the notch strip, three short points, and a Continue button." width="360"></p>

Loophole opens when you log in, so it is ready whenever Arduino IDE is. You can turn that off under **Open at login**.

Loophole keeps itself up to date. It downloads new versions in the background and installs them the next time it quits, usually when you restart or log out. It only installs versions that support your Mac's macOS.

### The helper

A small add-on inside Arduino IDE that lets Loophole read and correct Arduino IDE's board and port settings. Loophole adds it on first launch and keeps it up to date. Anyone who skipped it in version 1.0.0 gets it once, when Loophole updates. After an update, the card shows "Helper updated. Restart the IDE to finish." until Arduino IDE has been restarted once.

If you remove it, Loophole respects that and does not add it again. Instead it offers the helper where it would help:

- When a board's package is missing, the **Board package missing** card has an **Add helper** button. It puts the helper back and restarts Arduino IDE once, then the card offers **Install it for me**.
- Other cards show a quiet line with an **Add helper** button, since without the helper the wrong-port and wrong-board cards can never appear.

You can also add it back from the menu.

<p align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/nohelper-card.png?v=b2938d7b" alt="Open card reading Connected, UNO R4 WiFi, Ready to upload, with a line below: Add the IDE helper so I can also fix wrong ports, wrong boards and missing packages, and an Add helper button." width="420"></p>

| | Without | With |
| --- | --- | --- |
| Connected, No board, Cable, Power, Port busy | Yes | Yes |
| Fixes a wrong port | No | Yes |
| Detects a wrong board or missing package | No | Yes |
| Detects a frozen Arduino IDE | No | Yes |
| Model names for ESP32 boards and clones | Family only | The model chosen in Arduino IDE |
| Close Serial Monitor | Frees the port | Closes the tab too |
| Board not answering, Restart board, firmware update (UNO R4 WiFi) | Yes | Yes |

## Supported boards

Any board that appears on your Mac as a USB serial port.

<table>
<tr>
<td align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/ready-strip.png?v=ccc41bf1" alt="Teal board picture." width="230"><br>UNO, Mega</td>
<td align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/nano-strip.png?v=713909db" alt="Blue board picture." width="230"><br>Nano, MKR</td>
</tr>
<tr>
<td align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/esp32-strip.png?v=6cea983c" alt="Black board picture with a silver can." width="230"><br>ESP32</td>
<td align="center"><img src="https://raw.githubusercontent.com/IrtizaNasar/Loophole/main/docs/screenshots/pico-strip.png?v=e9238329" alt="Green board picture." width="230"><br>Raspberry Pi Pico</td>
</tr>
</table>

| Board | Name shown | Wrong board check | Package check |
| --- | --- | --- | --- |
| Official Arduino (UNO R3, UNO R4 Minima and WiFi, UNO Q, Mega 2560, Leonardo, Micro, Nano Every, Nano 33 IoT and BLE, Nano RP2040 Connect, Nano ESP32, Due, Zero, MKR1000, MKR WiFi 1010) | Exact, from the board | One-click switch | One-click install |
| Any other board Arduino IDE recognises, from an installed package or Arduino's online list | As Arduino IDE names it | Official Arduino boards only | Yes |
| ESP32 on built-in USB, Raspberry Pi Pico, Teensy | Family, then the model you choose in Arduino IDE | By family | Yes |
| Makers with their own USB id (Adafruit, SparkFun, Seeed, micro:bit) | Exact, from the installed board package; before that, as the board reports it | One-click switch once the package is installed | Yes |
| Clones with a CH340, CP210x or FTDI chip | The model chosen in Arduino IDE, or "board" | Limited | No |

The UNO R4 WiFi gets three extras: **Board not answering**, **Restart board** and the USB firmware update.

No tool can read the exact model of an ESP32 or a clone over USB. Arduino IDE has the same limit. Loophole does not guess: an unrecognised device is shown as "board". Monitors and phones that appear as serial ports are ignored.

### Two boards at once

Loophole follows the board you touched last: the one you plugged in most recently, or whose port you picked in Arduino IDE. When you plug a board in, Loophole also points Arduino IDE at it.

## Settings

Right-click the notch, or click the menu bar icon.

- **Check again now**
- **Restart Arduino IDE**
- **Update UNO R4 WiFi firmware…**: only while an UNO R4 WiFi with old USB firmware is plugged in.
- **Show on**: *Active screen* follows the screen you are working on (default). *Mac's built-in screen* keeps it on the notch.
- **Open at login**: on by default.
- **Check for Updates…**: Loophole also checks by itself once a day.
- **Install Arduino IDE helper…**
- **Quit Loophole**

The menu bar icon shows the state too: a filled hole is ready, an empty ring is no board, a dot above the hole needs you.

## Privacy

Loophole runs on your Mac. There is no account, and it never sends your sketches, files or anything that identifies you. What it looks at to do its job (your USB devices, ports and Arduino IDE's settings) stays on your Mac.

It sends anonymous usage statistics, so we can see how many Macs use Loophole and which problems come up most: a random ID made on your Mac, the versions of Loophole, macOS and Arduino IDE, which messages and fixes appeared, whether uploads and fixes worked, how long Arduino IDE was open, the kinds of board used, whether the Mac has a notch, and a rough location (country and city). Turn it off with **Share anonymous usage count** in the menu.

Otherwise it only goes online to check for its own updates, and when you press **Install it for me** or **Update firmware**, which use Arduino IDE's own installers.

## Questions

**Will it close my work?** Only when you press a button that says so. "Stop the …" and "Quit …" end the named program. "Restart Arduino IDE" closes every Arduino IDE window and reopens your sketch.

**Does it change anything by itself?** Only Arduino IDE's port setting, in every open window, the same as choosing it in Tools > Port. Restarting a board and updating its firmware only happen when you press the button.

**Does it work in full screen?** It stays hidden in full-screen apps unless something needs you.

**Does it check my code or wiring?** No. Green means the connection is good, not that the sketch compiles.

**How do updates work?** Loophole checks once a day, downloads a new version in the background, and installs it the next time it quits, usually when you restart or log out. It picks the newest version your macOS supports. Every update is signed, and Loophole refuses one that is not. To update straight away, choose **Check for Updates…** from the menu. Version 1.0.0 still asks first: press **Install Update** when its window appears.

**How do I remove it?** Quit Loophole and move it to the Bin. To remove the helper, delete `~/.arduinoIDE/plugins/loophole-bridge` and restart Arduino IDE.

## Limits

- One-click board switching covers official Arduino boards, and other makers' boards once their package is installed, when the board carries the maker's own USB id. Boards built on the ESP32 chip's own USB, or on a CH340 or CP210x chip, show as a family only: every maker's boards share those ids, so no software can tell them apart. One-click package install covers official Arduino boards.
- Wrong port, wrong board, missing package and frozen Arduino IDE fixes need the helper.
- Short-circuit detection is a strong hint, not a measurement.
- Board not answering, **Restart board** and the firmware update cover the UNO R4 WiFi, where this failure is common.
- With several Arduino IDE windows open, Loophole cannot always tell which one holds the Serial Monitor, so it warns whenever one does. The card follows the window you used last; until Arduino IDE has restarted once after an update, it follows the oldest window.
- Works with the Arduino IDE 2 family. Tested on 2.3.10, the current release. The helper needs 2.2 or later; on 2.0 and 2.1 Loophole runs without it. Arduino IDE 1 is not supported.
- VS Code, PlatformIO and the Arduino CLI are not supported, and there are no plans to add them.

## Why it exists

Loophole grew out of the physical computing module I teach at the UAL Creative Computing Institute. My students kept losing time to uploads that failed for reasons that had nothing to do with their code. Debugging those problems with them shaped every message in this app. I am sharing it so that other students, teachers, hobbyists and tinkerers can benefit too.

## Future

Loophole is a Mac app today. In future we plan to separate its diagnosis logic from the Mac interface and build a similar app for Windows, and potentially Linux. There is no date for this.

---

<sub>Updates are delivered with <a href="https://sparkle-project.org">Sparkle</a>, used under the MIT licence.</sub>

<sub>Loophole is an independent project. It is not affiliated with or endorsed by Arduino. Arduino is a trademark of Arduino SA.</sub>
