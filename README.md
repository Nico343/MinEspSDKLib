# Modifications
Translated the README from russian to english.

# MinEspSDK (meSDK)
Minimalist SDK on ESP8266ex v1.5.2
---

A complete set of Wi-Fi and [LwIP](http://savannah.nongnu.org/projects/lwip/) functions.<br><br>
It has a full set of functions for working with WiFi and UDP/TCP (LwIP ver1.4.0). This build does not contain espconn and SSL. It is designed to work with sensors and will include extensions for quick startup after deep-sleep with the ability to control further SDK loading or polling of sensors and a new transition to deep-sleep mode. In order to save power, the time from waking up after deep-sleep to the start of polling sensors and making a decision to go back to sleep or load the full SDK for communication and transmission of accumulated data will be 30-40 ms.

In the current version, with standard default settings, after a power-on, reset, or deep-sleep event, a TCP connection between a module in STATION mode with a fixed IP address and a module in SOFTAP mode is established in approximately no more than 540 ms. The main time is taken up by the SDK initialization in the WiFi part. Further, the half-duplex TCP traffic is more than 1 Megabyte per second.  

From [Espressif SDK](http://bbs.espressif.com/) ver 1.5.2 used only:<br> 
libpp.a, libwpa.a, libcrypto.a, libnet80211.a, parts libphy.a, user_interface.o<br><br>
Only the described parts from [Espressif SDK](http://bbs.espressif.com/) ver 1.5.2 are used.<br>
The remaining parts are provided with source code.<br>
LwIP based on [Open source LWIP for ESP_IOT_SDK_V1.4.0](http://bbs.espressif.com/viewtopic.php?f=46&t=1221).<br>

Supported options 48 kbytes IRAM.<br>
Supported '[Rapid Loader](https://github.com/pvvx/Rapid_Loader/)' and Flash 512 кbytes - 16 Mbytes.<br>
Support for extended IRAM memory of 48 kilobytes (USE_MAX_IRAM 48 option),
Flash memory from 512 kilobytes to 16 megabytes, and an SDK 'loader' for faster booting.

Free IRAM : 12 or 28 kbytes (option 48k IRAM)<br>
Free Heap : 55 kbytes<br>
Total Free RAM : 83 kbytes<br>

Options programming Flash:<br> 

SPI_SPEED: 40MHz or 80MHz.<br>
SPI_MODE: QIO only.<br>
FLASH_SIZE: Always set the size to 512 KB flash.<br>
			Automatic determination of the real size of the flash.
When flashing the firmware to the module, always set the Flash size to 512 kilobytes.
The actual Flash size is determined automatically during SDK startup.

The [Unofficial Developer Kit](http://esp8266.ru/forum/forums/devkit/) is used to compile the SDK.<br>

Three options are set in Eclipse's Manage Configurations:<br>
1. AutoMake (build the project for flashing, using Eclipse settings)<br>
2. CreateLib (build the libsdk.a library, using Eclipse settings)<br>
3. Default (build the project for flashing, using the makefile)<br>

The complete set for building the project using the SDK library includes:<br>
libsdk.a + [libmicroc.a](https://github.com/anakod/esp_microc) and include<br>     

