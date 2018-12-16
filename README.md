# MicroPython-Mac
MicroPython for Mac

# Python
Download：https://www.python.org/downloads/

install：python-3.7.1-macosx10.9.pkg

open Terminal

> python3 -V

Python 3.7.1



# ESPTOOL
use Terminal install packed(esptool)

$ sudo pip install esptool


sudo pip3 install --upgrade esptool

sudo pip3 install --list esptool

sudo pip3 install --uninstall esptool


# USB driver

Download：https://github.com/adrianmihalko/ch340g-ch34g-ch34x-mac-os-x-driver

install：CH34x_Install_V1.3.pkg


open Terminal

>ls -l /dev/tty.*

/dev/tty.wchusbserial1420


# MicroPython Firmware(ESP8266 .bin)

Download：http://micropython.org/download#esp8266

choose esp8266-20180511-v1.9.4.bin (latest)


# esptool

ESP8266 control board use before. Will execution erase flash ROM

$ esptool.py --port /dev/tty.wchusbserial1420 erase_flash (SLAB_USBtoUART = your port name)

Connecting....

...

Chip erase completed successfully in 7.2s

Hard resetting via RTS pin...



# ESP8266控制板燒錄.bin韌體檔

download esp8266-20180511-v1.9.4.bin file put user folder

$esptool.py --port /dev/tty.wchusbserial1420 --baud 115200 write_flash --flash_size=detect 0 esp8266-20180511-v1.9.4.bin

esptool.py v2.5.1

...

Hard resetting via RTS pin…


# 透過終端機操控MicroPython控制板

Mac use screen connect MicroPython control board

$screen /dev/tty.wchusbserial1420 115200

close screen:

press Ctrl+A+K > y


# 上傳程式檔到ESP8266控制板

安裝ampy

>sudo pip3 install adafruit-ampy

更新ampy

>sudo pip3 install adafruit-ampy --upgrade


# 啟用WebREPL

執行uPyCraft 

輸入

>import webrepl_setup


New password:12345678

Confirm password:12345678

Would you like to reboot now? (y/n)

y

webREPL daemon started on ws://192.168.4.1:8266


download webrepl.html file

https://github.com/micropython/webrepl

wifi connect you setting MicroPython-376e7f

執行webrepl.html

按下connect

# 設定ESP8266以STA(基站)模式連接無線網路

# 查找無線網路提供ip

將本機網路連結到同一 wifi ("ssid", "pwd")

執行uPyCraft輸入

>import network

>wlan = network.WLAN(network.STA_IF)

>wlan.active(True)

>wlan.connect("ssid", "pwd")

>wlan.ifconfig()

6-12
