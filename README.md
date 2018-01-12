# nrfutil

`nrfutil` is a Python package that includes the nrfutil command line utility
and the nordicsemi library.

This tool can be used used with the [Adafruit nRF52 Feather](https://www.adafruit.com/product/3406)
to flash firmware images onto the device using the simple serial port.

This library is written for Python 2.7.

# Installation

Run the following commands to make `nrfutil` available from the command line
or to development platforms like the Arduino IDE or CircuitPython:

**Notes** : Do **NOT** install nrfutil from the pip package (ex. `sudo pip
install nrfutil`). The latest nrfutil does not support DFU via Serial, and you
should install the local copy of 0.5.2 included with the BSP via the `python
setup.py install` command above.

### OS X and Linux

```
$ sudo pip install -r requirements.txt
$ sudo python setup.py install
```

### Windows

- Make sure that you have **Python 2.7** available on your system.
- Manually install **py2exe version 0.6.9** from this link (selecting
    the 32-bit or 64-bit version depending on your Python installation):
    (Download py2exe 0.6.9)[https://sourceforge.net/projects/py2exe/files/py2exe/0.6.9/].
- From the command prompt, install nrfutil via pip as follows:

```
pip install -r requirements.txt
python setup.py install
```

# Usage

To get info on usage of nrfutil:

```
nrfutil --help
```

To convert an nRF52 .hex file into a DFU pkg file that the serial bootloader
can make use of:

```
nrfutil dfu genpkg --dev-type 0x0052 --application firmware.hex dfu-package.zip
```

To flash a DFU pkg file over serial:

```
nrfutil dfu serial --package dfu-package.zip -p /dev/tty.SLAB_USBtoUART -b 115200
```