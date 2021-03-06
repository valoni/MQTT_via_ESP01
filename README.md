# MQTT_via_ESP01   
TCP/UDP Applicaton for UNO/MEGA/STM32 using ESP8266's AT firmware.   
You don't need Ethernet card.   
You need only ESP8266 module.   

__You can save flash & SRAM__   

_UNO+ENC28J60+UIPEthernet+PubSubClient_

```
Sketch uses 25090 bytes (77%) of program storage space. Maximum is 32256 bytes.
Global variables use 1736 bytes (84%) of dynamic memory, leaving 312 bytes for local variables. Maximum is 2048 bytes.
Low memory available, stability problems may occur.
```

_UNO+W5100+Ethernet+PubSubClient_

```
Sketch uses 19582 bytes (60%) of program storage space. Maximum is 32256 bytes.
Global variables use 1101 bytes (53%) of dynamic memory, leaving 947 bytes for local variables. Maximum is 2048 bytes.
```

_UNO+ESP01+Software Serial_

```
Sketch uses 9938 bytes (30%) of program storage space. Maximum is 32256 bytes.
Global variables use 897 bytes (43%) of dynamic memory, leaving 1151 bytes for local variables. Maximum is 2048 bytes.
```

---

**MQTT_Publish_ESP01**   
Simple Pubish Application.   
Supprted UNO/MEGA/STM32.   
It DON'T require any library.   

**MQTT_Subscribe_ESP01**   
Simple Subscribe Application.   
Supprted UNO/MEGA/STM32.   
It DON'T require any library.   

![slide1](https://user-images.githubusercontent.com/6020549/35101108-a13451d8-fca1-11e7-8cfd-37d71f18f880.JPG)

**Socket_Client_ESP01**   
Simple TCP/IP Client Application.   
Supprted UNO/MEGA/STM32.   
It DON'T require any library.   

**Socket_Server_ESP01**   
Simple TCP/IP Server Application.   
Supprted UNO/MEGA/STM32.   
It DON'T require any library.   

**Socket_Client_WiFiEsp**   
Simple TCP/IP Client Application using WiFiEsp.   
Supprted UNO/MEGA.   
It require Arduino WiFi library for ESP8266 modules.   
https://github.com/bportaluri/WiFiEsp   

**Socket_Server_WiFiEsp**   
Simple TCP/IP Server Application using WiFiEsp.   
Supprted UNO/MEGA.   
It require Arduino WiFi library for ESP8266 modules.   
https://github.com/bportaluri/WiFiEsp   

![slide2](https://user-images.githubusercontent.com/6020549/35101341-9019e394-fca2-11e7-9edd-0aa9086fd5db.JPG)

**NTP_Client_ESP01**   
Simple NTP Client Application.   
Supprted UNO/MEGA/STM32.   
It require Time library for Arduino.   
https://github.com/PaulStoffregen/Time   

**SNTP_Client_ESP01**   
Simple SNTP Client Application.   
Supprted UNO/MEGA/STM32.   
It DON'T require any library.   

![slide3](https://user-images.githubusercontent.com/6020549/35101499-241b1950-fca3-11e7-9876-0a22008ebc5a.JPG)

**SMTP_Client_gmail_ESP01**   
Simple SMTP Client Application.   
Supprted UNO/MEGA/STM32.   
It DON'T require any library.   
You need gmail account.   

![slide4](https://user-images.githubusercontent.com/6020549/35125598-90e2a360-fced-11e7-89ed-045cd6c49984.JPG)


# Flash AT firmware to ESP-01.   

![esp01-flash](https://user-images.githubusercontent.com/6020549/33159146-b8456238-d053-11e7-8202-a86cca2f8a3d.jpg)

I'm using esp8266_flasher.exe and v2.0 AT Firmware(ESP).bin.   

---

# Setup ESP-01 using terminal software such as CoolTerm.   

![esp01-setup](https://user-images.githubusercontent.com/6020549/33159150-bdade984-d053-11e7-9b93-bbbf05573441.jpg)

Connect to ESP-01 with 115200 bps.   

    AT+GMR
    AT version:0.40.0.0(Aug  8 2015 14:45:58)
    SDK version:1.3.0
    Ai-Thinker Technology Co.,Ltd.
    Build:1.3.0.2 Sep 11 2015 11:48:04
    OK
    
    AT+CWMODE=1
    
    OK
    AT+CWLAP
    +CWLAP:(3,"Picking",-86,"34:12:98:08:4b:4a",1,-4)
    +CWLAP:(4,"ctc-g-fa4a2e",-92,"c0:25:a2:b1:8c:2e",2,3)
    +CWLAP:(4,"aterm-e625c0-g",-49,"c0:25:a2:ac:cb:ba",3,15)
    +CWLAP:(1,"aterm-e625c0-gw",-48,"c2:25:a2:ac:cb:ba",3,15)
    
    OK
    
    AT+CWJAP="Your AP's SSID","Your AP's password"
    WIFI CONNECTED
    WIFI GOT IP
    
    OK
    
    AT+CIPSTA?
    +CIPSTA:ip:"192.168.10.142"
    +CIPSTA:gateway:"192.168.10.1"
    +CIPSTA:netmask:"255.255.255.0"
    
    OK
    AT+CWQAP
    
    OK
    
    WIFI DISCONNECT


_*** UNO ONLY ***_   
_*** Change baudrate to 4800bps ***_   
_*** Because there is no the 2nd UART in UNO ***_   
_*** So UNO use Software Serial with low speed ***_

    AT+UART_DEF=4800,8,1,0,0

Re-Connect to ESP-01 with 4800 bps.   

----

# Connect ESP-01 to UNO.

ESP-01(Tx) - UNO(D4)   
ESP-01(Rx) - UNO(D5)   

![ESP01-MQTT-UNO](https://user-images.githubusercontent.com/6020549/55268764-656f9f00-52d0-11e9-9120-360e397ffae0.jpg)

You can't use on-board 3.3V.    
An electric current is insufficient.   

----

# Connect ESP-01 to MEGA2560.

ESP-01(Tx) - MEGA(D19)   
ESP-01(Rx) - MEGA(D18)   

![ESP01-MQTT-MEGA](https://user-images.githubusercontent.com/6020549/55268794-9fd93c00-52d0-11e9-8cca-4f4bd202d745.jpg)

You can't use on-board 3.3V.    
An electric current is insufficient.   

----

# Connect ESP-01 to STM32F103(MAPLE Core).

ESP-01(Tx) - STM32F103(PA3)   
ESP-01(Rx) - STM32F103(PA2)   

![ESP01-MQTT-STM32F103_MAPLE-Core](https://user-images.githubusercontent.com/6020549/55272404-869bb400-52ff-11e9-97aa-1ff31090f925.jpg)

MAPLE Core.    
https://github.com/rogerclarkmelbourne/Arduino_STM32   

----

# Connect ESP-01 to STM32 NUCLEO(ST Core).

ESP-01(Tx) - STM32F103(PA10)   
ESP-01(Rx) - STM32F103(PA9)   

![ESP01-MQTT-STM32F103_ST-Core](https://user-images.githubusercontent.com/6020549/55272409-94e9d000-52ff-11e9-9f4b-61386ed3e656.jpg)

ST Core.    
https://github.com/stm32duino/Arduino_Core_STM32   

----

# Connect ESP-01 to STM32 F103 BluePill(ST Core).

ESP-01(Tx) - STM32F103(PA3)   
ESP-01(Rx) - STM32F103(PA2)   

![ESP01-MQTT-BLUEPILL_STM32F103_ST-Core](https://user-images.githubusercontent.com/6020549/62212468-c1ac1200-b3db-11e9-9fa2-9460d29b46cb.jpg)

Serial printing goes to PA9.   

----

# Connect ESP-01 to STM32 F103 MapleMini(ST Core).

ESP-01(Tx) - STM32F103(PA3)   
ESP-01(Rx) - STM32F103(PA2)   

![ESP01-MQTT-MAPLEMINI_STM32F103_ST-Core](https://user-images.githubusercontent.com/6020549/62213727-88c16c80-b3de-11e9-9f10-54a274908c4c.jpg)

Serial printing goes to PA9.   

----

# Connect ESP-01 to STM32 F303 BlackPill(ST Core).

ESP-01(Tx) - STM32F303(PA3)   
ESP-01(Rx) - STM32F303(PA2)   

Serial printing goes to PA9.   

----

# Connect ESP-01 to STM32 F401 BlackPill(ST Core).

ESP-01(Tx) - STM32F303(PA3)   
ESP-01(Rx) - STM32F303(PA2)   

Serial printing goes to PA9.   

----

# Connect ESP-01 to STM32 F4DISC1(ST Core).

ESP-01(Tx) - STM32F4DISC1(PD9)   
ESP-01(Rx) - STM32F4DISC1(PD8)   

I want to Fritzing Part of this board.   
Serial printing goes to PA2.   

----

# Connect ESP-01 to STM32 F407 development board that like DIYMORE F407VGT.

ESP-01(Tx) - STM32F103(PA3)   
ESP-01(Rx) - STM32F103(PA2)   

https://stm32-base.org/boards/STM32F407VGT6-diymore   
Serial printing goes to PA9.   

----

# How to Firmware Upate

1.Make sure TE(terminal equipment) is in sta or sta+ap mode   
    
    AT+CWMODE=3
    OK
    
2.Make sure TE got ip address   
    
    AT+CWJAP="ssid","12345678"
    OK
    
    AT+CIFSR
    192.168.1.134
    
3.Let's update   
    
    AT+CIUPDATE
    +CIPUPDATE:1    found server
    +CIPUPDATE:2    connect server
    +CIPUPDATE:3    got edition
    +CIPUPDATE:4    start start
    
    OK

----

Enjoy!!   

![esp01-mqtt-uno-tft](https://user-images.githubusercontent.com/6020549/33193265-cbbd2618-d10a-11e7-9dba-dd60643c27bb.JPG)


