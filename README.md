# ESP32-CAM-Video-Streaming-

Parts Required
 EP32-CAM with OV2640.
 FTDI programmer.
 Female-to-female jumper wires.

Introducing the ESP32-CAM
 The ESP32-CAM is a very small camera module with the ESP32-S chip that costs approximately $10. Besides the OV2640 camera, and several GPIOs to connect peripherals, it also features a microSD card slot that can be useful to store images taken with the camera or to store files to serve to client.

Features
Here is a list with the ESP32-CAM features:
  The smallest 802.11b/g/n Wi-Fi BT SoC module
  Low power 32-bit CPU,can also serve the application processor
  Up to 160MHz clock speed, summary computing power up to 600 DMIPS
  Built-in 520 KB SRAM, external 4MPSRAM
  Supports UART/SPI/I2C/PWM/ADC/DAC
  Support OV2640 and OV7670 cameras, built-in flash lamp
  Support image WiFI upload
  Support TF card
  Supports multiple sleep modes
  Embedded Lwip and FreeRTOS
  Supports STA/AP/STA+AP operation mode
  Support Smart Config/AirKiss technology
  Support for serial port local and remote firmware upgrades (FOTA)

ESP32-CAM Pinout
 There are three GND pins and two pins for power: either 3.3V or 5V.

 GPIO 1 and GPIO 3 are the serial pins. You need these pins to upload code to your board. Additionally, GPIO 0 also plays an important role, since it determines whether the ESP32 is in flashing mode or not. When GPIO 0 is connected to GND, the ESP32 is in flashing mode.

The following pins are internally connected to the microSD card reader:

   GPIO 14: CLK
   GPIO 15: CMD
   GPIO 2: Data 0
   GPIO 4: Data 1 (also connected to the on-board LED)
   GPIO 12: Data 2
   GPIO 13: Data 3

Video Streaming Server
 Follow the next steps to build a video streaming web server with the ESP32-CAM that you can access on your local network.
1. Install the ESP32 add-on
   In this example, we use Arduino IDE to program the ESP32-CAM board. So, you need to have Arduino IDE installed as well as the ESP32 add-on. Follow one of the next tutorials to install the ESP32 add-on, if you haven’t already:

2. CameraWebServer Example Code
In your Arduino IDE, go to File > Examples > ESP32 > Camera and open the CameraWebServer example.
Before uploading the code, you need to insert your network credentials in the following variables:

  const char* ssid = "REPLACE_WITH_YOUR_SSID";
  const char* password = "REPLACE_WITH_YOUR_PASSWORD";
Then, make sure you select the right camera module. In this case, we’re using the AI-THINKER Model.
So, comment all the other models and uncomment this one:

// Select camera model
//#define CAMERA_MODEL_WROVER_KIT
//#define CAMERA_MODEL_ESP_EYE
//#define CAMERA_MODEL_M5STACK_PSRAM
//#define CAMERA_MODEL_M5STACK_WIDE
#define CAMERA_MODEL_AI_THINKER

If none of these correspond to the camera you’re using, you need to add the pin assignment for your specific board in the camera_pins.h tab.
Now, the code is ready to be uploaded to your ESP32.

3. ESP32-CAM Upload Code
Connect the ESP32-CAM board to your computer using an FTDI programmer Many FTDI programmers have a jumper that allows you to select 3.3V or 5V. Make sure the jumper is in the right place to select 5V.

Important: GPIO 0 needs to be connected to GND so that you’re able to upload code.

ESP32-CAM	FTDI Programmer
GND	     GND
5V	     VCC (5V)
U0R	     TX
U0T    	 RX
GPIO 0	 GND

To upload the code, follow the next steps:

1) Go to Tools > Board and select AI-Thinker ESP32-CAM.

2) Go to Tools > Port and select the COM port the ESP32 is connected to.

3) Then, click the upload button to upload the code.

4) When you start to see these dots on the debugging window as shown below, press the ESP32-CAM on-board RST button.

After a few seconds, the code should be successfully uploaded to your board.

Getting the IP address
After uploading the code, disconnect GPIO 0 from GND.

Open the Serial Monitor at a baud rate of 115200. Press the ESP32-CAM on-board Reset button.

The ESP32 IP address should be printed in the Serial Monitor.

Accessing the Video Streaming Server
Now, you can access your camera streaming server on your local network. Open a browser and type the ESP32-CAM IP address. Press the Start Streaming button to start video streaming.
