# OLED Studio v3

**A web-controlled OLED display system built with ESP8266 NodeMCU and a
128×64 SH1106 OLED.**

OLED Studio lets you control and customize OLED content from a browser
over Wi-Fi. It combines embedded firmware with a browser-based interface
for displaying text, images, video, clocks, timers, weather information,
countdowns, and device details.

> **Note:** Read .

## Features

OLED Studio v3 includes **10 modes**:

1.  **Writing Board** --- Use the OLED as a writing board.
2.  **Video** --- Play visual content with dithering, brightness, and
    contrast controls.
3.  **Image** --- Display images with dithering.
4.  **Text** --- Display custom text.
5.  **Scrolling Text** --- Smoothly scroll text in different languages,
    including Tamil; scrolling runs on the ESP8266.
6.  **Weather** --- Display weather-related information.
7.  **Date & Time** --- Choose Classic, Big Digital, or Analog clock
    styles, with 12-hour or 24-hour time.
8.  **Timer / Stopwatch** --- Use countdown timers, Pomodoro presets,
    and a stopwatch. The OLED flashes **TIME UP** when a countdown
    finishes.
9.  **Event Countdown** --- Count down to a selected date with days and
    hh:mm:ss; the event is saved on the device.
10. **Device Info** --- View device information on the OLED.

### Additional capabilities

-   Browser-based control through the ESP8266's Wi-Fi connection.
-   Settings retained across reboots: brightness, 180° rotation, invert,
    idle dim, clock style, and event.
-   Keyboard shortcuts (`1`--`9` and `0`).
-   Over-the-air (OTA) updates, when supported by the computer and
    network setup.
-   Automatic I²C address detection for `0x3C` and `0x3D`.
-   Session and control improvements, including release control and
    takeover lockout.

## Hardware and software

-   **Microcontroller:** ESP8266 NodeMCU (ESP-12E)
-   **Display:** SH1106 OLED, 128×64
-   **IDE:** Arduino IDE 1.8.19
-   **Required Arduino library:** U8g2
-   **Web interface:** HTML, CSS, and JavaScript
-   **Firmware:** Arduino C++

## Installation

1.  Open the project folder named `OLED_Studio_v3`.
2.  Open `OLED_Studio_v3.ino` in Arduino IDE.
3.  Edit `credentials.h` and enter your Wi-Fi password. Configure the
    optional takeover PIN and OTA password if you want to use them.
4.  In Arduino IDE, select:
    -   **Board:** NodeMCU 1.0 (ESP-12E)
    -   **CPU Frequency:** 160 MHz
    -   **Flash Size:** 4 MB
5.  Install the **U8g2** library if it is not already installed.
6.  Connect the NodeMCU to your computer and upload the firmware over
    USB.
7.  Connect a browser device to the same Wi-Fi network and open the OLED
    Studio web interface using the IP address provided by the device.

A LittleFS upload is **not required** according to the project
instructions. OTA updates may be available later through **Tools → Port
→ `oledstudio`**, depending on your computer and network setup.

## OLED wiring

  OLED pin   NodeMCU pin
  ---------- -------------
  SDA        D2
  SCL        D1
  VCC        3.3 V
  GND        GND

## Troubleshooting

  -----------------------------------------------------------------------
  Problem                             What to try
  ----------------------------------- -----------------------------------
  OLED is blank                       Open Serial Monitor at `115200`
                                      baud to check the detected I²C
                                      address. Verify SDA is connected to
                                      D2, SCL to D1, and the display is
                                      powered at 3.3 V.

  Image looks garbled                 Set `I2C_CLOCK_HZ` to `100000` in
                                      the sketch.

  Clock stays on "Syncing time"       The ESP8266 needs internet access
                                      to synchronize time using NTP.

  Settings are not remembered         Settings are saved on the device.
                                      Make sure you have control of the
                                      session when changing them.
  -----------------------------------------------------------------------

## Updating the web interface

After editing `web/index.html`, regenerate the embedded web UI header
with:

``` bash
python tools/make_web_ui.py web/index.html web_ui.h
```

## License and usage

Copyright (c) 2026 Bharathvaasan A T. All rights reserved.

OLED Studio is provided under the **OLED Studio Personal Use License**,
not the MIT License.

Subject to the terms in the [`LICENSE`](LICENSE) file, individuals may
download, study, and use the software for personal, non-commercial
projects. Without prior written permission from the copyright holder,
redistribution of the original source code, sharing substantial portions
of the code, and distribution of modified versions or forks are not
permitted.

This is a custom, restrictive license; the project should not be
described as open-source software under the standard open-source
definition. Third-party libraries, dependencies, and assets may have
separate license terms that continue to apply.

Please read the complete [`LICENSE`](LICENSE) file before using the
project. The license does not override third-party license requirements.

## Repository description

OLED Studio is an ESP8266-based web-controlled OLED display project
featuring writing board, video and image display, custom and scrolling
text, weather information, multiple clock styles, timers, event
countdowns, and device information through a browser-based Wi-Fi
interface.
