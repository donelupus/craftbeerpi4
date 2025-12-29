# CraftBeerPi 4

[![Build](https://github.com/craftbeerpi/craftbeerpi4/actions/workflows/build.yml/badge.svg)](https://github.com/craftbeerpi/craftbeerpi4/actions/workflows/build.yml)
[![GitHub license](https://img.shields.io/github/license/craftbeerpi/craftbeerpi4)](https://github.com/craftbeerpi/craftbeerpi4/blob/master/LICENSE)
![GitHub issues](https://img.shields.io/github/issues-raw/craftbeerpi/craftbeerpi4)
![PyPI](https://img.shields.io/pypi/v/cbpi)
![Happy Brewing](https://img.shields.io/badge/CraftBeerPi%204-Happy%20Brewing-%23FBB117)

<p align="center">
  <img src="https://github.com/craftbeerpi/craftbeerpi4-ui/blob/main/cbpi4ui/public/logo192.png?raw=true" alt="CraftBeerPi Logo"/>
</p>

CraftBeerPi 4 is an open source software solution to control the brewing and
fermentation of beer :beer:.

## 📚 Documentation
Instructions on how to install CraftBeerPi and use its plugins is described
in the documentation, that can be found here: [gitbook.io](https://openbrewing.gitbook.io/craftbeerpi4_support/).

### Plugins
Plugins extend the base functionality of CraftBeerPi 4.
You can find a list of available plugins [here](https://openbrewing.gitbook.io/craftbeerpi4_support/master/plugin-installation#plugin-list).

## 🧑‍🤝‍🧑 Contribute
You want to help develop CraftBeerPi4? To get you quickly stated, this repository comes with a preconfigured
development environment. To be able to use this environment you need 2 things installed on your computer:

- docker
- visual studio code (vscode)

To start developing clone this repository, open the folder in vscode and use the _development container_ feature. The command is called _Reopen in container_. Please note that this quick start setup does not work if you want to develop directly on a 32bit raspberry pi os because docker is only available for 64bit arm plattform. Please use the regular development setup for that.

For a more detailed description of a development setup without the _development container_ feature see the documentation page:
[gitbook.io](https://openbrewing.gitbook.io/craftbeerpi4_support/)

### Contributors
Thanks to all the people who have contributed

[![contributors](https://contributors-img.web.app/image?repo=craftbeerpi/craftbeerpi4)](https://github.com/craftbeerpi/craftbeerpi4/graphs/contributors)


Offene Fragen:
* Wie kann man einen Aktor zeitlich steuern?
* Wie kann man einen Stellmotor auf Position ansteuern?
* Wie kann man eine Notifikation senden?


### Temperatur Sensor
1 wire enablen:
* Über raspi-config -> default pin 4 (BCM)
* Über /boot/firmware/config.txt
  dtoverlay=w1-gpio,gpiopin=5,pillup=on
  So kann jeder GPIO Pin verwendet werden. Aber z.B. i2c Pins können nicht ohne extra Konfiguration verwendet werden.

Unbedingt die 17 kOhm zwischen Data und VCC schalten. Ansonsten wurde kein Sensor angelegt.

3.3V an VCC hat gereicht und ist sehr wahrscheinlich auch besser, weil dann nur 3,3 V am GPIO Input anlegen.

Prüfe in ls /sys/bus/w1/devices  ob ein 28*** file angelegt wurde. Wenn Verbindung fehlerhaft, dann wird ein 00*** file angelegt.

Trotz mehmaligem Probieren, hat das Verwenden eines anderen Pins als Pin 4 erst nach einigen Versuchen funktioniert. Das ursprüngliche Problem wurde nicht gefunden. :(

### Level Sensor
Plugin war lange installiert aber Aktor war nicht verfügbar.
Installation via 

    pipx runpip cbpi4 install ./cbpi4-GPIODependentActor 

Ohne nachvollziehbaren Grund war der Aktor einfach plötzlich da.

Man muss den State des Aktors in der UI auf ON stellen!
Erst dann kann er den andern Aktor ausschalten.

## Waveshare Stepper Motor hat
https://www.waveshare.com/wiki/Stepper_Motor_HAT_(B)#wiringPi
Followed instructions BCM2835, wiringPi, lgpio, Python (pipx install RPi.GPIO)


### Temperatur Sensor
Nur default 1 wire GPIO PIN #4 hat funktioniert. Z.B. PIN # 17 hat nicht funktioniert.
Unbedingt die 17 kOhm zwischen Data und VCC schalten. Ansonsten wurde kein Sensor angelegt.
3.3V an VCC hat gereicht und ist sehr wahrscheinlich auch besser, weil dann nur 3,3 V am GPIO Input anlegen.


## Build and install a plugin locally

pipx runpip cbpi4 install <relative path to plugin source code folder>